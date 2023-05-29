---
title: "Sshfs"
date: 2023-05-29T18:27:30-04:00
draft: false
---

# Secure Shell File-System

## A utility for sending files through ssh or linking directories for continuous use

### Commands

Install sshfs. if you use ubuntu/debian:

    sudo apt-get install sshfs

or, if you use centos/rhel:

    sudo yum install fuse-sshfs

or, in macOS

    brew install sshfs

Create an empty dir

    mkdir /home/user/testdir

"link" or "mount" the two directories

    sshfs user@server.com:/remote/dir /home/user/testdir

"unlink" the dirs

    fusermount -u /home/user/testdir

On BSD and macOS, to unmount the filesystem:

    umount mountpoint

or

    diskutil unmount mountpoint

