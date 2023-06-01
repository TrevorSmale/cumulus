---
title: "Containers"
date: 2023-05-29T18:31:10-04:00
draft: false
---

<svg xmlns="http://www.w3.org/2000/svg" height="10em" viewBox="0 0 640 512"><!--! Font Awesome Free 6.4.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><style>svg{fill:#007BFF}</style><path d="M349.9 236.3h-66.1v-59.4h66.1v59.4zm0-204.3h-66.1v60.7h66.1V32zm78.2 144.8H362v59.4h66.1v-59.4zm-156.3-72.1h-66.1v60.1h66.1v-60.1zm78.1 0h-66.1v60.1h66.1v-60.1zm276.8 100c-14.4-9.7-47.6-13.2-73.1-8.4-3.3-24-16.7-44.9-41.1-63.7l-14-9.3-9.3 14c-18.4 27.8-23.4 73.6-3.7 103.8-8.7 4.7-25.8 11.1-48.4 10.7H2.4c-8.7 50.8 5.8 116.8 44 162.1 37.1 43.9 92.7 66.2 165.4 66.2 157.4 0 273.9-72.5 328.4-204.2 21.4.4 67.6.1 91.3-45.2 1.5-2.5 6.6-13.2 8.5-17.1l-13.3-8.9zm-511.1-27.9h-66v59.4h66.1v-59.4zm78.1 0h-66.1v59.4h66.1v-59.4zm78.1 0h-66.1v59.4h66.1v-59.4zm-78.1-72.1h-66.1v60.1h66.1v-60.1z"/></svg>

# OCI

OCI (Open Container Initiative) is a standard for container image format and runtime that enables interoperability across different container platforms. It provides a common language for building, packaging, and running containerized applications, ensuring portability and ease of deployment.

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

### Namespaces

### Control Groups

### Union Mounts

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

# Podman
A OCI based container engine created by RedHat that is mostly interchangeable with Docker with some key differences

## Podman is slightly different

* Podman is an alternative to Docker that uses the same command line interface (CLI) and the same container image format.
* Unlike Docker, Podman does not require a daemon to be running in order to manage and run containers.
* Podman uses the same container runtime as CRI-O and Buildah, which is runc.
* Podman supports rootless containers, which means that it can run containers without requiring the user to have root privileges.
* Podman does not have the daemon attack surface and does not have any daemon-specific configuration options.
* Podman does not support Swarm mode, which is Docker's built-in container orchestration.
* Podman can be used with Kubernetes, which is a popular container orchestration platform.
* Podman support many features like cgroups v1 and v2, namespaces, and SELinux that are not available in Docker.

## Example CLI build command

podman build -t myhugo:latest --build-arg HUGO_VERSION=0.78.2 -f Dockerfile .

## Trouble pulling images from Fedora/Redhat container directories

There is seemingly an issue with pulling container images from the suggested sources. I am working from Fedora 37 and this issue seems to stem from permission issues or build scripts. I will be looking into this at a later date.

## Able to build from Docker.io

So I have successfully pulled down/built containers with vertualized open ports from the Docker.io hub. This works similarly to my past Docker experiences.
I can use the $PS command to see built and running containers. furthermore, I can stop and remove the running contianers with the same CLI commands as well.







