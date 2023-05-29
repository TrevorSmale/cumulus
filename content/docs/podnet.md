---
title: "Podman Pod Networking"
date: 2023-05-29T17:55:58-04:00
draft: false
---

# Configuring container networking with Podman

Podman uses two different means for its networking stack, depending on whether the container is rootless or rootfull. When rootfull, defined as being run by the root (or equivalent) user, Podman primarily relies on the containernetworking plugins project. When rootless, defined as being run by a regular user, Podman uses the slirp4netns project.

## Networking and Podman pods

By definition, all containers in a Podman pod share the same network namespace. This fact means that they will have the same IP address, MAC addresses, and port mappings. You can conveniently communicate between containers in a pod by using localhost.

## Rootfull networking

When the Podman package is installed, a default network configuration is commonly installed into /etc/cni/net.d as 87-podman-bridge.conflist. In addition, the default network name is defined in /usr/share/containers/libpod.conf with the key cni_default_network. In an unaltered libpod.conf, the default network name will be that of the default configuration provided by the package. You can copy the libpod.conf file to /etc/containers/libpod.conf if you want to alter any of its default settings.

To create a new network for rootfull containers, use the podman network command. You can customize the network with the command flags or by editing it by hand afterward. The podman network create command provides you with the newly created network configuration file path:

```bash
$ sudo podman network create
/etc/cni/net.d/cni-podman4.conflist


