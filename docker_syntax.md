#### List Docker CLI commands
```
docker container --help
```

#### Display Docker version and info
```
docker --version
docker version
docker info
```

#### Build an image and tag it with a name. We have to stand in the working directory
```
docker build -t root/newname .
```

#### Run the image. Port 4000 is in the browser, port 8080 is in Dockerfile (mapping port 4000 to 8080)
```
docker run -p 4000:8080 root/newname
```

#### Run the image in detached mode (in the background)
```
docker run -d -p 4000:8080 root/newname
```

#### Publish port / redirects a public port to a private port inside the container
```
-p
```

#### Run already existing image
```
docker run >imageID or name<
```

#### List Docker images
```
docker image ls
docker image ls -a ## List all images on this machine
```

#### Remove specified image from local machine
```
docker image rm >imageID or name<
```

#### List Docker containers (running, all, all in quiet mode)
```
docker container ls
docker container ls -all
docker container ls -a -q 
```

#### List the contents of the root director in the container
```
ls
```

#### Create container by running the image in the background.
```
docker run -d -rm -p 4000:8080 >imageID or name<
-d   ## detached mode (runs in the background)
-rm  ## remove the container after running
```

#### Create container by running the image in the background and giving it a name.
```
docker run -d --name >newcontainername< -p 4000:8080 >imageID or name<
```

#### Stops and starts a container running
```
docker stop >containerID or name<
docker start >containerID or name<
```

#### Add name to the container during running.
```
--name
```

#### Use an environment variable to specify the root password 
```
-e
```

#### Displays the images
```
docker image ls
```

#### List running containers
```
docker container ls
```

#### List running and non-running containers
```
docker container ls --all
```

#### Force shutdown of the specified container
```
docker container kill >containerID or name<
```

#### Remove specified container from this machine
```
docker container rm >containerID or name<
```

#### Log in this CLI session using your Docker credentials
```
docker login
```

#### Tag image for upload to registry
```
docker tag >imageID or name< username/repository:tag   ## find out a name for the repository, tag is optional
```

#### Upload tagged image to registry
```
docker push username/repository:tag
```

#### Pull image from Docker Hub
```
docker pull username/repository:tag
```

#### Run image from a registry    
```
docker run username/repository:tag
```

#### Run image previously was pulled
```
docker run -p 4000:8080 username/repository:tag
```

#### Step inside the container
```
docker exec -it >containerID or name< /bin/bash
```

#### Exit from the commandline of the container
```
exit
```

#### Shows running containers
```
docker ps
```

#### Delete a container
```
docker container rm >containerID or name<
```

#### Delete an image
```
docker image rm >imageID or name<
```

#### Display ip address in Linux
```
ip addr show
```

#### Show running processes,
```
ps aux
```

#### Link an application image with a database image
```
docker run -p 8080:8080 --name >database image< --link testdatabase:mysql -d >application image<
```
