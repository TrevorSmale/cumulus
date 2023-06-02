---
title: "Containers"
date: 2023-05-29T18:31:10-04:00
draft: false
---

<svg xmlns="http://www.w3.org/2000/svg" height="10em" viewBox="0 0 640 512"><!--! Font Awesome Free 6.4.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><style>svg{fill:#007BFF}</style><path d="M349.9 236.3h-66.1v-59.4h66.1v59.4zm0-204.3h-66.1v60.7h66.1V32zm78.2 144.8H362v59.4h66.1v-59.4zm-156.3-72.1h-66.1v60.1h66.1v-60.1zm78.1 0h-66.1v60.1h66.1v-60.1zm276.8 100c-14.4-9.7-47.6-13.2-73.1-8.4-3.3-24-16.7-44.9-41.1-63.7l-14-9.3-9.3 14c-18.4 27.8-23.4 73.6-3.7 103.8-8.7 4.7-25.8 11.1-48.4 10.7H2.4c-8.7 50.8 5.8 116.8 44 162.1 37.1 43.9 92.7 66.2 165.4 66.2 157.4 0 273.9-72.5 328.4-204.2 21.4.4 67.6.1 91.3-45.2 1.5-2.5 6.6-13.2 8.5-17.1l-13.3-8.9zm-511.1-27.9h-66v59.4h66.1v-59.4zm78.1 0h-66.1v59.4h66.1v-59.4zm78.1 0h-66.1v59.4h66.1v-59.4zm-78.1-72.1h-66.1v60.1h66.1v-60.1z"/></svg>

{{< panel title="Containers" style="info" >}}

Containers are a lightweight virtualization technology that enables the efficient and isolated execution of software applications. They encapsulate an application and its dependencies, including libraries, frameworks, and configuration files, into a portable and self-contained unit. By using containerization, applications can be deployed and run consistently across different computing environments, regardless of the underlying infrastructure. Containers provide a high level of abstraction, allowing developers to package their code into a standardized format and ensuring that it operates reliably across diverse systems. With their fast startup times, low overhead, and scalability, containers have revolutionized software development, deployment, and scaling by promoting portability, efficiency, and flexibility in modern computing ecosystems.

{{< /panel >}}

{{< panel title="OCI" style="info" >}}

OCI (Open Container Initiative) is a standard for container image format and runtime that enables interoperability across different container platforms. It provides a common language for building, packaging, and running containerized applications, ensuring portability and ease of deployment.

{{< /panel >}}

{{< panel title="Docker" style="info" >}}

Docker is an open-source platform that simplifies the deployment and management of applications by providing containerization technology. It enables developers to package an application and its dependencies into a lightweight, isolated container, ensuring consistent and reproducible deployments across different environments. Docker provides a flexible and scalable solution, allowing applications to run seamlessly on any host system. With its efficient resource utilization and fast startup times, Docker revolutionizes software development and deployment by promoting portability, collaboration, and efficient utilization of computing resources. It has become a cornerstone in modern software development workflows and infrastructure management, empowering developers to build, ship, and run applications with ease.

{{< /panel >}}

{{< panel title="Podman" style="info" >}}

Docker is an open-source platform that simplifies the deployment and management of applications by providing containerization technology. It enables developers to package an application and its dependencies into a lightweight, isolated container, ensuring consistent and reproducible deployments across different environments. Docker provides a flexible and scalable solution, allowing applications to run seamlessly on any host system. With its efficient resource utilization and fast startup times, Docker revolutionizes software development and deployment by promoting portability, collaboration, and efficient utilization of computing resources. It has become a cornerstone in modern software development workflows and infrastructure management, empowering developers to build, ship, and run applications with ease.

{{< /panel >}}


# Docker
Course notes taken while following the Docker Mastery course by Bret Fisher
Course if by: Bret Fisher Youtube [https://www.youtube.com/@BretFisher]

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

    docker stop + first 3 - 4 characters of unique id

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

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg
   xmlns:dc="http://purl.org/dc/elements/1.1/"
   xmlns:cc="http://creativecommons.org/ns#"
   xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
   xmlns:svg="http://www.w3.org/2000/svg"
   xmlns="http://www.w3.org/2000/svg"
   id="svg8"
   version="1.1"
   viewBox="0 0 228.25899 61.226642"
   height="231.40778"
   width="862.71112">
  <defs
     id="defs2">
    <marker
       style="overflow:visible"
       id="marker5584"
       refX="0"
       refY="0"
       orient="auto">
      <path
         transform="scale(0.2)"
         style="fill:#4d4d4d;fill-opacity:1;fill-rule:evenodd;stroke:#4d4d4d;stroke-width:1.00000003pt;stroke-opacity:1"
         d="M 0,-7.0710768 -7.0710894,0 0,7.0710589 7.0710462,0 Z"
         id="path5582" />
    </marker>
    <marker
       style="overflow:visible"
       id="DiamondS"
       refX="0"
       refY="0"
       orient="auto">
      <path
         transform="scale(0.2)"
         style="fill:#4d4d4d;fill-opacity:1;fill-rule:evenodd;stroke:#4d4d4d;stroke-width:1.00000003pt;stroke-opacity:1"
         d="M 0,-7.0710768 -7.0710894,0 0,7.0710589 7.0710462,0 Z"
         id="path5359" />
    </marker>
    <marker
       style="overflow:visible"
       id="DotL"
       refX="0"
       refY="0"
       orient="auto">
      <path
         transform="matrix(0.8,0,0,0.8,5.92,0.8)"
         style="fill:#4d4d4d;fill-opacity:1;fill-rule:evenodd;stroke:#4d4d4d;stroke-width:1.00000003pt;stroke-opacity:1"
         d="m -2.5,-1 c 0,2.76 -2.24,5 -5,5 -2.76,0 -5,-2.24 -5,-5 0,-2.76 2.24,-5 5,-5 2.76,0 5,2.24 5,5 z"
         id="path5335" />
    </marker>
    <clipPath
       id="clipPath81511"
       clipPathUnits="userSpaceOnUse">
      <rect
         y="-1.4835175"
         x="934.65692"
         height="12.832292"
         width="26.19375"
         id="rect81513"
         style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:#a7a9ac;stroke-width:0.52916664;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1" />
    </clipPath>
  </defs>
  <metadata
     id="metadata5">
    <rdf:RDF>
      <cc:Work
         rdf:about="">
        <dc:format>image/svg+xml</dc:format>
        <dc:type
           rdf:resource="http://purl.org/dc/dcmitype/StillImage" />
        <dc:title></dc:title>
      </cc:Work>
    </rdf:RDF>
  </metadata>
  <g
     transform="translate(-1170.4453,517.6202)"
     id="layer1">
    <g
       id="g163426" />
    <g
       id="g10819"
       transform="translate(0,-285.75012)">
      <g
         id="text10671"
         style="font-style:normal;font-weight:normal;font-size:37.59195328px;line-height:22.55517006px;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#892ca0;fill-opacity:1;stroke:none;stroke-width:0.26458332px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1"
         aria-label="podman">
        <path
           id="path80700"
           style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:Montserrat;-inkscape-font-specification:Montserrat;fill:#892ca0;fill-opacity:1;stroke-width:0.26458332px"
           d="m 1249.8778,-209.9329 c -3.1202,0 -5.526,1.27812 -6.9921,3.60883 v -3.45846 h -4.3231 v 27.29175 h 4.3231 v -10.75129 c 1.4661,2.3307 3.8719,3.60882 7.0673,3.60882 5.7139,0 9.4731,-4.09752 9.4731,-10.07464 0,-6.0899 -3.8719,-10.22501 -9.5483,-10.22501 z m -0.9022,16.61564 c -3.5713,0 -6.0899,-2.66903 -6.0899,-6.541 0,-3.75919 2.5186,-6.46581 6.0899,-6.46581 3.5712,0 6.0899,2.74421 6.0899,6.46581 0,3.83438 -2.5187,6.541 -6.0899,6.541 z" />
        <path
           id="path80702"
           style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:Montserrat;-inkscape-font-specification:Montserrat;fill:#892ca0;fill-opacity:1;stroke-width:0.26458332px"
           d="m 1272.4964,-209.9329 c -6.2027,0 -10.4506,4.09752 -10.4506,10.14983 0,6.01471 4.2479,10.14982 10.4506,10.14982 6.1651,0 10.413,-4.13511 10.413,-10.14982 0,-6.05231 -4.2479,-10.14983 -10.413,-10.14983 z m 0,3.7216 c 3.5712,0 6.0899,2.63144 6.0899,6.46582 0,3.87197 -2.5187,6.50341 -6.0899,6.50341 -3.6088,0 -6.1275,-2.63144 -6.1275,-6.50341 0,-3.83438 2.5187,-6.46582 6.1275,-6.46582 z" />
        <path
           id="path80704"
           style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:Montserrat;-inkscape-font-specification:Montserrat;fill:#892ca0;fill-opacity:1;stroke-width:0.26458332px"
           d="m 1302.1564,-217.67684 v 11.35277 c -1.466,-2.33071 -3.8719,-3.64642 -7.1048,-3.64642 -5.6388,0 -9.5108,4.09752 -9.5108,10.11223 0,6.0899 3.8344,10.2626 9.5859,10.2626 3.1954,0 5.6012,-1.27812 7.0297,-3.60882 v 3.42086 h 4.3231 v -27.89322 z m -6.1275,24.47236 c -3.6464,0 -6.1274,-2.70662 -6.165,-6.50341 0.038,-3.83438 2.5562,-6.57859 6.165,-6.57859 3.6089,0 6.1275,2.70662 6.1275,6.57859 0,3.79679 -2.5186,6.50341 -6.1275,6.50341 z" />
        <path
           id="path80706"
           style="fill:#60605b"
           d="m 1339.1334,-209.9329 c -3.6464,0 -6.3154,1.46608 -7.5936,4.81177 -0.9398,-3.04495 -3.3832,-4.81177 -6.9545,-4.81177 -3.3081,0 -5.8643,1.20294 -7.2552,4.02234 v -3.87197 h -4.2855 v 19.99891 h 4.2855 v -9.88668 c 0,-3.49605 2.1051,-6.12749 5.5636,-6.24026 2.9322,0 4.699,1.842 4.699,4.88695 v 11.23999 h 4.3231 v -9.88668 c 0,-3.49605 2.0675,-6.12749 5.4884,-6.24026 2.9321,0 4.7366,1.842 4.7366,4.88695 v 11.23999 h 4.323 v -12.44293 c 0,-4.77418 -2.7442,-7.70635 -7.3304,-7.70635 z" />
        <path
           id="path80708"
           style="fill:#60605b"
           d="m 1368.4916,-189.78362 -0.038,-13.11959 c -0.038,-4.39826 -2.9322,-7.02969 -8.0823,-7.02969 -3.7968,0 -5.8268,0.86461 -8.6086,2.51866 l 1.7669,3.00736 c 1.9923,-1.35332 3.9847,-2.02997 5.9019,-2.02997 3.1577,0 4.7742,1.50368 4.7742,4.02234 v 0.60147 h -6.0523 c -4.8118,0.0376 -7.556,2.36829 -7.556,6.01471 0,3.53365 2.7066,6.20267 7.0297,6.20267 2.8946,0 5.1877,-0.86461 6.6162,-2.63143 v 2.44347 z m -9.9619,-3.2329 c -2.4059,0 -3.872,-1.16535 -3.872,-2.96977 0,-1.91719 1.3157,-2.66903 4.1351,-2.66903 h 5.4133 v 1.84201 c -0.2256,2.18033 -2.5939,3.79679 -5.6764,3.79679 z" />
        <path
           id="path80710"
           style="fill:#60605b"
           d="m 1385.9695,-209.9329 c -3.3833,0 -5.9396,1.20294 -7.3681,3.98474 v -3.83437 h -4.323 v 19.99891 h 4.323 v -10.63852 c 0.3008,-3.12013 2.3683,-5.41324 5.6764,-5.45083 3.0074,0 4.8118,1.842 4.8118,4.84936 v 11.23999 h 4.3231 v -12.44293 c 0,-4.77418 -2.7818,-7.70635 -7.4432,-7.70635 z" />
      </g>
    </g>
    <g
       id="g10987"
       transform="translate(-4.0076941e-7,-285.75012)">
      <g
         id="g10985"
         transform="translate(238.41304,-199.74894)">
        <path
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
           d="m 963.98321,-1.2653795 h 12.72207"
           id="path10821" />
        <path
           id="path10823"
           d="m 966.09989,1.3804536 h 12.72207"
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
        <g
           style="stroke-width:0.86916679"
           transform="matrix(1.1500458,0,0,1.1510087,-143.9252,0.43908228)"
           id="g10875">
          <path
             id="path10825"
             d="m 973.10356,3.3983398 c -2.30839,-3.74257021 -1.79145,-7.3525044 -2.88299,-12.510239 -0.59897,-3.1855248 -2.62142,-5.8149598 -5.25403,-6.7776908 -2.17189,-0.757647 -6.68263,-0.759955 -8.59472,0 -2.63261,0.962731 -4.65498,3.592166 -5.25395,6.7776908 -1.09155,5.1577346 -0.57458,8.76766879 -2.88297,12.510239"
             style="fill:#cccccc;fill-opacity:1;fill-rule:evenodd;stroke:#000000;stroke-width:0.68990111;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
          <ellipse
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1"
             id="ellipse10827"
             cx="966.56354"
             cy="-4.1070371"
             rx="1.1158856"
             ry="1.1746163" />
          <ellipse
             ry="1.1746163"
             rx="1.1158856"
             cy="-4.1070371"
             cx="955.28723"
             id="ellipse10829"
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1" />
          <g
             id="g10839"
             style="stroke:#a7a9ac;stroke-width:0.51800275;stroke-miterlimit:4;stroke-dasharray:none"
             transform="matrix(0.88789899,0,0,0.88789899,108.02196,0.55783395)">
            <path
               id="path10831"
               d="m 956.41893,-5.9814347 -4.67056,1.2514712"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10833"
               d="m 956.9481,-5.2538306 -4.6966,2.711577"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10835"
               d="m 957.34497,-4.3939348 -4.7625,4.76249998"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10837"
               d="m 957.5434,-3.2694556 -2.434,4.21584432"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
          </g>
          <g
             transform="matrix(-0.88789899,0,0,0.88789899,1814.1581,0.55783389)"
             style="stroke:#a7a9ac;stroke-width:0.51800275;stroke-miterlimit:4;stroke-dasharray:none"
             id="g10849">
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 956.41893,-5.9814347 -4.67056,1.2514712"
               id="path10841" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 956.9481,-5.2538306 -4.6966,2.711577"
               id="path10843" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 957.34497,-4.3939348 -4.7625,4.76249998"
               id="path10845" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.51800275;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 957.5434,-3.2694556 -2.434,4.21584432"
               id="path10847" />
          </g>
          <ellipse
             style="opacity:1;fill:#ffffff;fill-opacity:1;stroke:#60605b;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1"
             id="ellipse10851"
             cx="961.04285"
             cy="-4.9292688"
             rx="3.5825801"
             ry="3.4063873" />
          <ellipse
             transform="scale(-1,1)"
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10853"
             cx="-966.52734"
             cy="-7.8406329"
             rx="1.7252614"
             ry="1.7690334" />
          <path
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.68990105;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             d="m 968.07427,-11.544209 c -0.34474,-0.448317 -0.89334,-0.733231 -1.45836,-0.757402 -0.53344,-0.02282 -1.07281,0.185834 -1.45201,0.561706"
             id="path10855" />
          <g
             id="g10863"
             style="stroke-width:0.77700406;stroke-miterlimit:4;stroke-dasharray:none"
             transform="matrix(0.88789899,0,0,0.88789899,106.61242,0.08798743)">
            <g
               id="g10861"
               transform="translate(0,-0.52916667)"
               style="stroke-width:0.77700406">
              <path
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:0.77700406;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
                 d="m 962.30591,-5.7829972 0.0993,1.9843749 c 0,0 1.58751,1.4221355 2.51355,-0.033073 0,0 -0.0993,-0.8268214 -0.16541,-1.0914047"
                 id="path10857" />
              <path
                 id="path10859"
                 d="m 962.28751,-5.7829972 -0.0993,1.9843749 c 0,0 -1.58751,1.4221355 -2.51355,-0.033073 0,0 0.0993,-0.8268214 0.16541,-1.0914047"
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:0.77700406;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            </g>
          </g>
          <path
             id="path10865"
             style="fill:#808080;fill-opacity:1;stroke:#000000;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             d="m 962.57174,-5.5436767 c -0.1202,-0.3110186 -0.1202,-0.9330691 -0.48062,-0.9330691 -0.36047,0 -0.69372,-0.2332673 -1.04826,-0.2332673 -0.35456,0 -0.68781,0.2332673 -1.04828,0.2332673 -0.36046,0 -0.36046,0.6220505 -0.48061,0.9330691 -0.1202,0.3110253 1.52889,1.3218472 1.52889,1.3218472 0,0 1.64903,-1.0108219 1.52888,-1.3218472 z" />
          <ellipse
             ry="1.7690334"
             rx="1.7252614"
             cy="-7.8406329"
             cx="955.36047"
             id="ellipse10867"
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <ellipse
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10869"
             cx="954.78467"
             cy="-8.3384542"
             rx="0.8483994"
             ry="0.88143349" />
          <path
             id="path10871"
             d="m 953.81353,-11.544209 c 0.34474,-0.448315 0.89333,-0.73323 1.45835,-0.757402 0.53344,-0.02282 1.07281,0.185833 1.45201,0.561706"
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.68990105;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <ellipse
             ry="0.88143349"
             rx="0.8483994"
             cy="-8.3384542"
             cx="965.94666"
             id="ellipse10873"
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.68990111;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
        </g>
        <path
           id="path10877"
           d="m 948.21183,4.2931494 h 32.92765"
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
        <g
           style="stroke-width:1.20411575"
           transform="matrix(0.83048493,0,0,0.83048493,164.55035,-1.4237955)"
           clip-path="url(#clipPath81511)"
           id="g10929">
          <path
             id="path10879"
             d="m 958.31594,13.737399 c -0.26199,-1.782196 -0.38924,-3.720848 -0.8727,-6.0017375 -0.53058,-2.8174518 -2.32212,-5.1430676 -4.65415,-5.9945597 -1.92393,-0.6701043 -5.91966,-0.6721461 -7.61343,0 -2.33204,0.8514921 -4.1235,3.1771079 -4.65409,5.9945597 -0.48346,2.2808895 -0.61071,4.2195415 -0.87269,6.0017375"
             style="fill:#cccccc;fill-opacity:1;fill-rule:evenodd;stroke:#000000;stroke-width:0.95576686;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
          <ellipse
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1"
             id="ellipse10881"
             cx="954.20367"
             cy="12.16224"
             rx="0.98848081"
             ry="1.0388949" />
          <ellipse
             ry="1.0388949"
             rx="0.98848081"
             cy="12.16224"
             cx="944.21478"
             id="ellipse10883"
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1" />
          <g
             id="g10893"
             style="stroke:#a7a9ac;stroke-width:0.81074655;stroke-miterlimit:4;stroke-dasharray:none"
             transform="matrix(0.7865243,0,0,0.7853064,193.68501,16.288101)">
            <path
               id="path10885"
               d="m 956.41893,-5.9814347 -4.67056,1.2514712"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10887"
               d="m 956.9481,-5.2538306 -4.6966,2.711577"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10889"
               d="m 957.34497,-4.3939348 -4.7625,4.76249998"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10891"
               d="m 957.5434,-3.2694556 -2.434,4.21584432"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
          </g>
          <g
             transform="matrix(-0.7865243,0,0,0.7853064,1705.0252,16.288101)"
             style="stroke:#a7a9ac;stroke-width:0.81074655;stroke-miterlimit:4;stroke-dasharray:none"
             id="g10903">
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 956.41893,-5.9814347 -4.67056,1.2514712"
               id="path10895" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 956.9481,-5.2538306 -4.6966,2.711577"
               id="path10897" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 957.34497,-4.3939348 -4.7625,4.76249998"
               id="path10899" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.81074655;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 957.5434,-3.2694556 -2.434,4.21584432"
               id="path10901" />
          </g>
          <ellipse
             style="opacity:1;fill:#ffffff;fill-opacity:1;stroke:#60605b;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1"
             id="ellipse10905"
             cx="949.31329"
             cy="11.435012"
             rx="3.1735437"
             ry="3.0127952" />
          <ellipse
             transform="scale(-1,1)"
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10907"
             cx="-954.17163"
             cy="8.8600426"
             rx="1.528282"
             ry="1.5646298" />
          <path
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.9557668;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             d="m 955.54199,5.5843938 c -0.30575,-0.3965787 -0.79155,-0.6484892 -1.29185,-0.6698876 -0.4724,-0.020205 -0.95006,0.1642901 -1.28623,0.4968037"
             id="path10909" />
          <g
             id="g10917"
             style="stroke-width:1.21611977;stroke-miterlimit:4;stroke-dasharray:none"
             transform="matrix(0.7865243,0,0,0.7853064,192.4364,15.872544)">
            <g
               style="stroke-width:1.21611977"
               id="g10915"
               transform="translate(0,-0.52916667)">
              <path
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:1.21611977;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
                 d="m 962.30591,-5.7829972 0.0993,1.9843749 c 0,0 1.58751,1.4221355 2.51355,-0.033073 0,0 -0.0993,-0.8268214 -0.16541,-1.0914047"
                 id="path10911" />
              <path
                 id="path10913"
                 d="m 962.28751,-5.7829972 -0.0993,1.9843749 c 0,0 -1.58751,1.4221355 -2.51355,-0.033073 0,0 0.0993,-0.8268214 0.16541,-1.0914047"
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:1.21611977;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            </g>
          </g>
          <path
             id="path10919"
             style="fill:#808080;fill-opacity:1;stroke:#000000;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             d="m 950.66771,10.891591 c -0.10648,-0.275082 -0.10648,-0.825257 -0.42575,-0.825257 -0.31931,0 -0.61451,-0.2063147 -0.92858,-0.2063147 -0.31407,0 -0.60928,0.2063147 -0.92858,0.2063147 -0.31932,0 -0.31932,0.550175 -0.42575,0.825257 -0.10647,0.275088 1.35433,1.169114 1.35433,1.169114 0,0 1.46076,-0.894026 1.35433,-1.169114 z" />
          <ellipse
             ry="1.5646298"
             rx="1.528282"
             cy="8.8600426"
             cx="944.27972"
             id="ellipse10921"
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <ellipse
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10923"
             cx="943.76965"
             cy="8.4197426"
             rx="0.75153452"
             ry="0.77958798" />
          <path
             id="path10925"
             d="m 942.90945,5.5843938 c 0.30575,-0.3965787 0.79155,-0.6484892 1.29185,-0.6698876 0.4724,-0.020205 0.95006,0.1642901 1.28623,0.4968037"
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.9557668;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <ellipse
             ry="0.77958798"
             rx="0.75153452"
             cy="8.5291576"
             cx="953.76178"
             id="ellipse10927"
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.95576686;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
        </g>
        <path
           style="opacity:1;fill:none;fill-opacity:1;stroke:#892ca0;stroke-width:1.0583334;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
           d="m 961.97165,23.28467 -19.29817,-9.23285 -4.82036,-20.8616002 13.2871,-16.7806158 21.38926,-0.06408 13.38485,16.7011458 -4.69887,20.8897002 z"
           id="path10931" />
        <path
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
           d="m 943.44933,8.5264827 h 19.83144"
           id="path10933" />
        <path
           id="path10935"
           d="m 952.87074,12.492952 h 27.50208"
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
        <g
           transform="translate(0.78045403,0.88370984)"
           id="g10979">
          <path
             style="fill:#cccccc;fill-opacity:1;fill-rule:evenodd;stroke:#000000;stroke-width:0.79374999;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
             d="m 977.46866,11.110796 c -0.23262,-1.5824091 -0.34561,-3.3037374 -0.77487,-5.3289381 -0.4711,-2.5016132 -2.06181,-4.566525 -4.13242,-5.32256411 -1.70825,-0.59498494 -5.25606,-0.59679785 -6.75995,0 -2.07062,0.75603911 -3.66125,2.82095091 -4.13236,5.32256411 -0.42927,2.0252007 -0.54225,3.746529 -0.77486,5.3289381"
             id="path10937" />
          <ellipse
             ry="0.92243373"
             rx="0.87767112"
             cy="9.7122078"
             cx="973.81744"
             id="ellipse10939"
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1" />
          <ellipse
             style="opacity:1;fill:#e7e8e9;fill-opacity:1;stroke:none;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1"
             id="ellipse10941"
             cx="964.9483"
             cy="9.7122078"
             rx="0.87767112"
             ry="0.92243373" />
          <g
             transform="matrix(0.69835413,0,0,0.69727276,299.02348,11.966021)"
             style="stroke:#a7a9ac;stroke-width:0.7583214;stroke-miterlimit:4;stroke-dasharray:none"
             id="g10947">
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.7583214;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 955.74614,-3.9599306 -4.67056,1.2514712"
               id="path10943" />
            <path
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.7583214;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
               d="m 956.27531,-3.2323265 -4.6966,2.71157695"
               id="path10945" />
          </g>
          <g
             id="g10953"
             style="stroke:#a7a9ac;stroke-width:0.7583214;stroke-miterlimit:4;stroke-dasharray:none"
             transform="matrix(-0.69835413,0,0,0.69727276,1640.4712,13.375562)">
            <path
               id="path10949"
               d="m 956.41893,-5.9814347 -4.67056,1.2514712"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.7583214;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
            <path
               id="path10951"
               d="m 956.9481,-5.2538306 -4.6966,2.711577"
               style="fill:none;fill-rule:evenodd;stroke:#a7a9ac;stroke-width:0.7583214;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
          </g>
          <ellipse
             ry="2.6750579"
             rx="2.8177862"
             cy="9.0665035"
             cx="969.47528"
             id="ellipse10955"
             style="opacity:1;fill:#ffffff;fill-opacity:1;stroke:#60605b;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:5.99999952;stroke-opacity:1" />
          <ellipse
             ry="1.3892332"
             rx="1.3569601"
             cy="6.7801905"
             cx="-973.789"
             id="ellipse10957"
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             transform="scale(-1,1)" />
          <path
             id="path10959"
             d="m 975.00567,3.8717489 c -0.27147,-0.3521218 -0.70281,-0.575793 -1.14703,-0.5947926 -0.41945,-0.01794 -0.84356,0.1458731 -1.14204,0.4411116"
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.79374993;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <g
             transform="matrix(0.69835413,0,0,0.69727276,297.44499,13.006589)"
             style="stroke-width:1.13748205;stroke-miterlimit:4;stroke-dasharray:none"
             id="g10967">
            <g
               transform="translate(0,-0.52916667)"
               id="g10965"
               style="stroke-width:1.13748205">
              <path
                 id="path10961"
                 d="m 962.30591,-5.7829972 0.0993,1.9843749 c 0,0 1.58751,1.4221355 2.51355,-0.033073 0,0 -0.0993,-0.8268214 -0.16541,-1.0914047"
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:1.13748205;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
              <path
                 style="fill:none;fill-rule:evenodd;stroke:#000000;stroke-width:1.13748205;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
                 d="m 962.28751,-5.7829972 -0.0993,1.9843749 c 0,0 -1.58751,1.4221355 -2.51355,-0.033073 0,0 0.0993,-0.8268214 0.16541,-1.0914047"
                 id="path10963" />
            </g>
          </g>
          <path
             d="m 970.6778,8.5840058 c -0.0945,-0.2442451 -0.0945,-0.7327449 -0.37802,-0.7327449 -0.28351,0 -0.54562,-0.1831865 -0.82448,-0.1831865 -0.27887,0 -0.54098,0.1831865 -0.82449,0.1831865 -0.28352,0 -0.28352,0.4884998 -0.37802,0.7327449 -0.0945,0.2442506 1.20251,1.0380563 1.20251,1.0380563 0,0 1.297,-0.7938057 1.2025,-1.0380563 z"
             style="fill:#808080;fill-opacity:1;stroke:#000000;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="path10969" />
          <ellipse
             style="fill:#000000;fill-opacity:1;stroke:#892ca0;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10971"
             cx="965.00598"
             cy="6.7801905"
             rx="1.3569601"
             ry="1.3892332" />
          <ellipse
             ry="0.69219536"
             rx="0.66728675"
             cy="6.3892479"
             cx="964.5531"
             id="ellipse10973"
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1" />
          <path
             style="fill:none;fill-opacity:1;stroke:#000000;stroke-width:0.79374993;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             d="m 963.78925,3.8717489 c 0.27148,-0.3521208 0.70281,-0.5757916 1.14703,-0.5947926 0.41945,-0.017942 0.84357,0.1458717 1.14205,0.4411116"
             id="path10975" />
          <ellipse
             style="fill:#ffffff;fill-opacity:1;stroke:none;stroke-width:0.79374999;stroke-linecap:square;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="ellipse10977"
             cx="973.4754"
             cy="6.4801154"
             rx="0.66728675"
             ry="0.69219536" />
        </g>
        <path
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
           d="m 950.75405,15.138787 h 12.72207"
           id="path10981" />
        <path
           id="path10983"
           d="m 958.16237,17.784622 h 10.477"
           style="fill:none;fill-rule:evenodd;stroke:#3c6eb4;stroke-width:1.05833328;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1" />
      </g>
    </g>
  </g>
</svg>

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







