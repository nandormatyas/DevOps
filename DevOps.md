# Malachite - Húlí Operations  



## Our server - Edward the I.

We use a local server with Ubuntu 17.10 Server Edition installed on it. 

The service manager tool for this OS is **[systemd](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)** (in case you are looking for solutions on forums) !!!

Docker and OpenSSH are already installed on the machine.

There is a persistent and fully operational Jenkins instance running in a Docker container 0/24.

MAC address: **d4:3d:7e:a7:71:db** 

On the 120th wall plug the machine gets a static Internet IP which is: **195.228.147.126**

The port of the Jenkins instance: **9090**

The public domain for Húlí Jenkins is http://jenkins.greenfoxacademy.com

The local IP of the server from the 'Office' network: **10.27.6.163**

The port of the Jenkins instance: **9090**

### You can use OpenSSH if you want to login to the server. 

The username for Edward is: cristal

The hostname is the static Internet or Ethernet IP.

The port is **22701** for the static Internet IP, and **22** for the local address.

`sudo ssh -p 22701 kristaly@195.228.147.126`

or 

`sudo ssh -p 22 kristaly@10.27.6.163`

### Docker?

**The HÚLÍ Server machine has Docker installed on it!**

But if you want to install Docker in any another environment you should use these links:

[Windows Install](https://docs.docker.com/docker-for-windows/install/)

[Mac Install](https://docs.docker.com/docker-for-mac/install/ )

[Ubuntu Linux Install](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

### Jenkins

**The instance on the Húlí server is up and running!!!**

If you install one for yourself, on the first loading, Jenkins will ask for a security token.

To get the token, you have to login to your container with the command below:

`docker exec -it ${jenkins_container_name} /bin/bash` 

than

`cat /var/jenkins_home/secrets/initialAdminPassword`

copy the hashed code and use it to startup Jenkins.

### AWS
Amazon Web Services will be our bread and butter, find  the related guide [here](AWS.md)

Find the Angular-frontend guide [here](Angular_Frontend_DevOps.md)

### Useful Tools
[ngrok](https://ngrok.com/)\
Tunnel local server to public Internet

[tmux](https://gist.github.com/henrik/1967800)\
Terminal Multiplexer
