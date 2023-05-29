---
title: "Docker"
date: 2023-05-29T18:28:29-04:00
draft: false
---

# Docker
## Course notes taken while following the Docker Mastery course by Bret Fisher

## What is Docker?
### Docker is container engine

## The 3 Major functions of Docker

* The docker image - Build
* The docker registry - Ship
* The docker container - Run

## Containers and the Cloud

* The cloud native computing foundation is based around a containerized workflow.
* The container image is kind of like a universal package manager.
* Dockerfile/Container image Anatomy - OCI standard for container images.
* The OCI ‘Open Container Initiative’ 

## Anatomical/Layers of the docker file called ‘stanzas’ are written in JSON
### All of these stanzas together are called a docker image.

* FROM python
* RUN pip install flask
* WORKDIR /app
* COPY ..
* CMD python app.py

## Docker Registries

* The Docker image registry is for the app distribution 
* Each image has a unique SHA hash that represents the unique data within

## Running a Docker image

When an image is run using docker run, the Docker engine will prioritize and place it within a container with its own namespace and IP address. It essentially runs like its own system.

## Container Networking

Containers name space are air gapped from one another by default. So additional commands must be used in order to specify/setup open ports.

## Practice Space

Labs.play-with-docker.com

## Simple Commands

### PS

Processes running

### Docker pull 

will pull a docker image and dependancies using the docker engine. The engine is able to pull images from many different places

## Concepts from Linux

### NAMESPACES

### Control Groups

### UNION MOUNTS

## Why Docker and Containers?

* Isolation
* Environments
* Speed

## Technological progress of development infrastructure

* 90’s saw the exit from mainframes
* 00’’s Saw a change from bare metal to virtual
* 10’s Saw Datacenter to Cloud
* Now Host to Container (Serverless)

## Advantages of containerization

* Develop, Build, Test and Deploy Faster.
* Weekly live Q&A sessions on YouTube 

## Bret Fisher Youtube [https://www.youtube.com/@BretFisher]

## Creating and using containers

Checking the version of Docker and associated infrastructure:

CLI: Docker Version, always used first to verify the status and version

CLI: Docker Info, displays most configuration values of the current docker install

Check all available commands:

CLI: Docker

There is now a hierarchy of commands

This means there are now management and common commands

## Difference between an image and Container

* An image is the application we want to run
* A container is an instance of that image running as a process
* You can have many containers running off the same image
* In this lecture our image will be the Nginx web server
* Dockers default image "registry" is called Docker Hub (hub.docker.com)

## Running an Nginx container

CLI: docker container run --publish 80:80 nginx

* Downloaded image 'nginx' from Docker Hub
* Started a new container from that image
* Opened port 80 on the host IP
* Routes that traffic to the container IP, port 80

Note: you will get a "bind" error if the left number [Host port] is already in use. If this is the case, an easy alternative is 8888

## Viewing container status in the CLI

docker container ls - will show regular status

docker container ls -a - will show additional info

## Stopping a running container

Docker stop + first 3 - 4 characters of unique id

## Naming a container

docker container run --publish 80:80 --detach --name webhost nginx

## See the process running within a container

docker container top 'name'

## Remove containers

docker container rm 'id' 'id' 'id'

Note: error thrown if one or more of the containers are running

## What happens in the background when 'docker container run' command is run

1. Looks for that image locally in image cache, doesn't find anything
2. Then looks in remote image repo (defaults to Docker Hub)
3. Downloads the latest version (nginx:latest by default)
4. Creates new container based on that image and prepares to start
5. Gives it a virtual IP on a private network inside docker engine
6. Opens up port 80 on host and forwards to port 80 in container
7. Starts container by using the CMD in the image Dockerfile

## Containers vs. VM's

Containers are not Mini VM's

* They are just processes
* Limited to what resources they can access
* Exit when process stops

by using a process viewing tool, one can see the docker process among other processes.

docker ps will display docker specific processes
ps will display that docker process mixed in with all of the processes of the operating system.

## Finding help

CLI docker --help

or

[docs.docker.com]

## Managing Multiple Containers

The objective is to run multiple containers here. 
Each one should be on their own port

1. nginx
2. MariaDB
3. httpd (Apache)

each will be on their own port

* Nginx on 80:80
* MariaDB on 3306:3306
* httpd on 8080:80

docker container run --publish 80:80 --detach --name nginx nginx
docker container run --publish 3306:3306 --detach -e MYSQL_ROOT_PASSWORD=secret --name db mariadb:latest
docker container run --publish 8080:80 --detach --name apache httpd

## Docker inspection of stats

* docker container top - process list in one container
* docker container inspect - details of one container config
* docker container stats - performance stats for all containers

## Getting a Shell Inside Containers

* docker container run -it - start new container interactively
* docker container exec -it - run additional command in existing container
* Different Linux distros in containers

We don't need to have an SSH server within the container in order to remote in. Docker allows us to start both (Interactivity) and a (tty) service

When starting a container:

docker container run [options] IMAGE [COMMAND] [ARG]

example: docker container run -it --name proxy nginx bash

## How to access a container after the fact

We can utilize the docker container exec command with 2 or more arguments to effect the container after it is created.

for example docker container exec -it db bash will create a bash shell in the root of this database container.

## Alpine linux is super small and has its own package manager

In fact, Alpine is soooo small that it does not include BASH, it actually containes SH

So starting up an alpine container with an open shell looks like this

docker container run -it alpine sh

APK is the package manager for alpine

## Docker Networks: Concepts

* Review of docker container run -p
* For local dev/testing, networks ususally "just work"
* Quick port check with docker container port <contianer>
* Learn concepts of Docker Networking
* Understand how network packets move around Docker

## Docker Networks Defaults

* Each container connected to a private virtual network "bridge"
* Each virtual network routes through NAT firewall on host IP
* All containers on a virtual network can talk to each other without -p
* Best practice is to create a new virtual network for each app:
    * network "my-web-app" for mysql and php/apache containers
    * network "my_api" for mongo and node-js containers
* "Batteries Included, But Removable"
    * Defaults work well in many cases, but easy to swap out parts to customize it
* Make new virtual Networks
* Attach containers to more then one virtual network (or none)
* Skip virtual networks and use host IP (--net=host)
* Use different Docker network drivers to gain new abilities
* and much more...

## Diving into network interfaces

docker container run -p 80:80 --name web-host -d nginx

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' web-host

docker creates a bridge network or docker0 that is a virtual network. Internal addresses are hidden to external traffic.

## Docker Networks: CLI Management

* Show networks: docker network ls
* Inspect a network: docker network inspect
* Create a network: docker network create --driver
* attach a network to container: docker network connect
* Detach a network from container: docker network disconnect

## Docker networks: Default Security

* Create your apps so frontend/backend sit on same Docker network
* Their inter-communication never leaves host
* All externally exposed ports closed by default
* You must manually expose via -p, which is better default security!










