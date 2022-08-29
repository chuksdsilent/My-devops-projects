# Docker

In Docker we isolate our services like ngnix, tomcat, apache etc. To isolate our services we need VM's/Cloud Computing to setup infra. We isolate our service in OS. Because of isolation we end up setting up multiple VM's/Instances VM's/Instances will be overprovisioned and results in high CapEx and OpEx. Docker is container virtual environment. Docker manages container. Docker hub is the registry of docker images.
### Every VM needs

* OS and OS needs maintenance
* OS also needs Licensing
* OS also Takes time to boot

VM's are portable(i.e it can be moved to server or to local) but they are bulky. VM's also need s alot of resources

### Point to note

* isolating services are important
* high availablity achived by multiple instances/vm's
* portability matters or eases the deployment

## Container
Container share the machines' OS system kernel and therefore do not require OS per application

A container is a standard unit of software that packages up 
* code
* dependencies
* but does not use different operating systems

### Comparing VM vs Containers

* container uses one operating system while vms uses different operating systems
* container boot up faster than vms
* container are processes
* container offer isolation while vms offer virtualization
* containers are OS virtualization
* VM are are hardware virualization


A stopped container is like vm images consist of multiple layers. Containers run from images

## Docker Image
A Docker image is a file used to execute code in a Docker container. Docker images act as a set of instructions to build a Docker container, like a template. Docker images also act as the starting point when using Docker. An image is comparable to a snapshot in virtual machine (VM) environments. Images are called repositories in registry. Docker hub is a default registry

### Different Registries

* Cloud based Registry
* Dockerhub
* GCR(Google Container Registry)
* Amazon ECR

* Inhouse or Local Registry
* Nexus 3+
* JFrog Artifacotory
* DTR (Docker Trusted Registry)


Docker Commands

To test docker
```
docker run hello-world
```

To see active containers
```
docker ps
```

To see all(active and dead) containers
```
docker ps -a
```

To pull nginx with the latest version
```
docker pull nginx
```

To see all images
```
docker images
```

To run a docker image
```
docker run --name oshnginx -p 7932:80 -v -d nginx
-v = volume
-d(Detached Mode) = run in the background
7932 = container port
80 = host port
```
To stop a container
```
docker stop container-id
```

To start a container
```
docker start container-id or container-name
```

To see all files inside a docker image
```
docker exec image-name ls /
```

To attach/login into docker images
```
docker exec -it image-name /bin/bash or /bin/sh
```
To update the image
```
apt update
```
To install process comman
```
apt install procps -y
```
To see all the process inside the container
```
ps -ef
```
To remove images
```
docker rmi image-name:tag
```
To stop the container
```
docker stop container-name/id
```

To remove container
```
docker rm container-name/id
```

To see detailed information about an image
```
docker inspect container-name
```
To show the logs of a container
```
docker logs container-name
```
## DOCKER VOLUMES

Docker is volatile (it is disposable).

Docker is not stateful

To make a container stateful ( like mysql that stores data) 

We can achieve this in two ways

* Volumes in the host location. Managed by docker in /var/lib/docker/volumes/ on linux machines

To create a volume
```
docker volume create volume-name
docker run --name db01 -e MYSQL_ROOT_PASSWORD=admin -d -p3030:3306 -v volume-name:/var/lib/mysql mysql:5.7
```

* Bind Mounts
   This sync a folder between docker container and the host machine like sync directory in vagrant

To create a bind mount
```
docker run --name db01 -e MYSQL_ROOT_PASSWORD=admin -d -p3030:3306 -v /home/oshabz/vprodbdata:/var/lib/mysql mysql:5.7
```

DOCKER IMAGES

Create Docker Images
We use Dockerfile to create images

* From => Base Image
* LABEL => Adds metadata to an image
* RUN => execute commands in a new layer and commit the results
* ADD/COPY => Adds files and folder into image
* CMD => Runs binaries/commands on docker run
* ENTRYPOINT => Allows you to configure a container that will run as an executable
* VOLUME => Creates a mount point marks it as holding externally mounted volumes
* EXPOSE => Container listens on the specified network ports at runtime
* ENV => set the environment variable
* USER => Sets the username (or UID)
* WORKDIR => Sets the working directory
* ARG => Defines a variable that uses can pass at build-time
* ONBUILD => Adds to the images trigger instruction to be executaed at a later time

To build a docker image
```
docker build -t nanoweb .
```
To push image to docker registry
login using
```
docker login
```
Enter username and password

Build the image with your username
```
docker build -t oshabz/nanoweb .
```

To run command on Dockerfile
```
CMD ["echo", "hello"]
```
Entry Point
The user needs to pass an argument
```
ENTRYPOINT ["echo"]
```
if CMD and ENTRYPOINT are used in together the CMD becomes the default

To tar a directory
cd into the directory
```
tar czvf name.tar.gz *
```




