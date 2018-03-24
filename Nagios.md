# NAGIOS

>Nagios /ˈnɑːɡiːoʊs/, now known as Nagios Core, is a free and open source >computer-software application that monitors systems, networks and infrastructure. >Nagios offers monitoring and alerting services for servers, switches, applications >and services. It alerts users when things go wrong and alerts them a second time >when the problem has been resolved.


You can reach our Nagios for HULI devs on our server in the inner network on [this](10.27.6.163:7700) address.

Login: nagiosadmin
Password: nagios


This graphical user interface is not for setup purposes!!! You can use it only for monitoring.
At the moment the DevOps team offers two types of monitoring solutions. 
The **check_ping** method for basic pinging, and the **check_http_content** that can check the heartbeat endpoints for one particular string data. 

If you want to set up a new host app that you want to monitor you have to send a template to the DevOps team with the data below:

- URL of the webapp
- specify the name of the endpoint 
- the string you want to check for



### FOR DevOps team members:


You have to set up the new hosts via cfg files inside the nagios docker on the server.
So first use *ssh* to get into the server machine.
Then *exec* into the docker container with the 
```sudo docker exec -it <containerID> /bin/bash```.

Here you have to focus on the  ```~/opt/nagios /etc#```folder

and on the ```/opt/nagios/etc/nagios.cfg file.```


**1.**  Make a new **<nameofyourhosty>.cfg** file inside the ```~/opt/nagios/etc#``` folder.

**2.** Use the huli developer`s data to fill out this form and copy into the new cfg file

```
define host{
        use                     linux-server
        host_name               <nameofyourhost>
        alias                   <aliasoyyourhost>
        address     			<URL of your app without / and without endpoint specified>
s.com
       }

define service{
        use                             generic-service
        host_name                       <nameofyourhost>
        service_description             PING
        check_command                   check_ping!100.0,20%!500.0,60%
        }


define service{
        use                             generic-service
        host_name                       <nameofyourhost>
        service_description             HTTP
        check_command                   check_http_content!<url with endpoint>!<the string you checking for>!<an int number to set time>
        notifications_enabled           <1 for enable notification 0 for disable it>
```

**3.** Navigate to **nagios.cfg** file and add this line into it:

```cfg_file=/opt/nagios/etc/objects/<newhostfile>.cfg```


**4.** Run the ```nagios -v /opt/nagios/etc/nagios.cfg``` command to check if the modifications are correct or not.

**5.** Restart the docker.

**6.** Login to Nagios on the web interface.
