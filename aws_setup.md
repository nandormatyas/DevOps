# Set Up Your Project To AWS
___________________

## Prerequisites

You should have 4 files now:

- Dockerfile  → this builds your image
- A program file (JS, C#...)
- For JS →  package.json
- .dockerignore

Build your app with docker.
________

## App deploy preparation

Create a file named Dockerrun.aws.json, it should look something like this:
```JSON
{     
  "AWSEBDockerrunVersion": "1",          
  "Image":{       
    "Name": "docker_username/docker_image_name"        ←_docker_repository     
  },     
    "Ports": [       {         
      "ContainerPort": "8080",            ←_docker_image_port
      "hostPort": "80"                ←_port_to_reach_on
    }     
  ]   
}
```
______________
## App deployment

In your aws account go to “services” → “Compute/Elastic Beanstalk” → upper right corner “Create New Application” 

1. Name your application
2. Choose “create web server”
3. “Predefined configuration:” → choose “Docker”
4. “Environment type:” → “single instance”
5. Upload your dockerrun.aws.json
6. You can leave all other stuff default

And there you go!
