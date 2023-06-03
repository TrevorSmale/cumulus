+++
title = "Kubernetes"
description = "Kubernetes Notes"
weight = 2
+++
{{< panel title="Update Log" style="success" >}}

* 2023 06 02 - Initial Commit

{{< /panel >}}

{{< panel title="WIP" style="danger" >}}
This site is a work in progress, notes are being actively added, formatted and reorganized at the moment.
{{< /panel >}}

{{< lead >}}
Kubernetes is an open-source container orchestration platform that simplifies the management and scaling of containerized applications. It automates the deployment, scaling, and management of containers across clusters of nodes. With Kubernetes, users can define desired states and let the platform handle the complexities of resource allocation, load balancing, and fault tolerance. It provides features for automatic scaling, service discovery, rolling updates, and self-healing. Kubernetes promotes portability, allowing applications to run consistently across different environments. It has become the de facto standard for container orchestration, enabling efficient management of containerized workloads and facilitating the development of scalable and resilient applications.
{{< /lead >}}

---

### What it does

* It Automates deployments
* Scales workloads
* Manages workloads
* Provides infrastructore for hosting workloads

---

## Origin

### How Kubernetes came into existance

K8's was originally created by google, then opened sourced.

---

## Pods

### What is a pod?

* It is a wrapper for containers
* By creating pods, one can assure that the containers within the pod will all be compatable with the host
* Allows one to create a taxonomy of the containers

---

## Controller

### What is a Controller?

* It is was drives the activity of sinular and multiple pods

What is a Service?

* Service is a port exposure
* It is exposed through the Kube proxy
* The proxy will connect to an external port eg. 80

---

## Presequisites

### Things to know before learning Kubernetes

Before beginning Kubernetes it is essential to have proficiency in the following:

* Linux Bash Command Line
* Git and GitHub for Source Management
* CommonMark Markdown
* Bash Scripting (Shellcheck)
* JSON / YAML
* Go Template Language
* Web Essentials (HTML, CSS, Plain JS, DOM, HTTP)
* Networking and Network Troubleshooting
* Using and Creating Containers with 'Docker' and 'Dockerfile'
* No need to learn Docker compose.

---

## How to learn Kubernetes

### Prioritized order for learning Kubernetes

1. Kubernetes component architecture and communication
2. Get familiar with all standard Kubernetes resources
3. Use kind to deploy a simple app

### There are some prerequisites to learning Kubernetes before getting started

* Containers must be well understood
* persistant volumes and databases must be well understood
* Networking must be well understood

---

## There are some catches when it comes to containers

* when containers are destroyed the files within them are destroyed, so seperate persistant volumes must be created.
* Containers & Pods must be on the same network in order to interoperate.
* Kubernetes may close/kill pods for efficiency purposes.

---

## The Docker Part is actually easy

* One can create a network with Docker
* One can create a persistant volume with Docker
* One can easily pull premade docker files that are static or managed

---
