---
title: "Skool"
Description: "Building out an interactive online school for effective remote training"
date: 2023-08-01
draft: false
---

# How it started

Over the years, I have been involved in delivering both in-person and online courses, using a range of Learning and Course Management tools such as Evernote, Excel, GitHub, and others. While I have managed to make these solutions work for my needs, I have come to realize that they are not ideal for creating a seamless and efficient learning environment.

As part of my journey to enhance my applied IT skills, I delved into the world of self-hosting and explored various solutions like VMs, LXC containers, and Docker containers. After conducting thorough research, I recognized the potential of building a fast and efficient online school for both Synchronous and Asynchronous Learning through self-hosting.

As I explored available options, I came across Moodle, the most popular open-source Learning Management System (LMS). While it is not written in Golang as I initially hoped, it is still an excellent solution for my requirements. Its feature-rich nature and open-source flexibility make it an attractive choice.

For this project, I aim to create a portable, repeatable, quick, and secure environment to host the Moodle LMS. After evaluating various approaches, I have chosen to utilize containers to achieve this goal. Containers provide an isolated and lightweight environment for applications, making it easier to deploy and manage the LMS. To further improve the security and flexibility of my setup, I have chosen to work with Podman over Docker as my container engine.

By using a Podman pod, which is a networked group of containers, I can orchestrate and manage my online school more effectively. To define this environment, I will leverage Podman Compose, a tool similar to Docker Compose but tailored for Podman.

Overall, this project aims to leverage the power of containers, particularly Podman, to create a self-hosted and efficient online learning platform using Moodle. I am excited to explore this path as it aligns with my goal of enhancing my IT skills while providing an optimal learning experience for students in both synchronous and asynchronous modes.

# How its going

I have been diligently working on crafting this Podman Compose YAML file, which, when executed, can seamlessly build and deploy the entire project from scratch. This approach aligns perfectly with our goal of using a portable, repeatable, fast, and secure environment for hosting the application.

To ensure both speed and security, I have made use of alpine-based container images, which are lightweight and efficient. Additionally, I have implemented a secure virtual network within the pod, providing an extra layer of protection for our applications.

With this setup, we can confidently deploy our project in a reliable and consistent manner, making it easy to replicate and scale when needed. By leveraging the power of Podman and its ability to orchestrate containers efficiently, we can create a robust environment for our applications to thrive.

# The Compose file:

    version: '1'
    services:
    postgres:
        image: docker.io/alpine:3.18
        restart: unless-stopped
        command: ["postgres"]
        environment:
        - POSTGRES_PASSWORD=moodle
        # PostgreSQL username
        - POSTGRES_USER=moodle
        # PostgreSQL database name
        - POSTGRES_DB=moodle
        volumes:
        - postgres:/var/lib/postgresql/data
        networks:
        - MOODLE-NETWORK

    moodle:
        image: erseco/alpine-moodle
        restart: unless-stopped
        environment:
        - LANG=en_US.UTF-8
        - LANGUAGE=en_US:en
        - SITE_URL=http://localhost
        # Moodle database type (PostgreSQL)
        - DB_TYPE=pgsql
        # PostgreSQL hostname (service name of the postgres container)
        - DB_HOST=postgres
        # PostgreSQL port
        - DB_PORT=5432
        # Moodle database name
        - DB_NAME=moodle
        # Moodle database username
        - DB_USER=moodle
        # Moodle database password
        - DB_PASS=moodle
        # Moodle database table prefix
        - DB_PREFIX=mdl_
        # Whether to use SSL proxy or not
        - SSLPROXY=false
        # Moodle administrator's email address
        - MOODLE_EMAIL=user@example.com
        # Default Moodle language
        - MOODLE_LANGUAGE=en
        # Site name for Moodle instance
        - MOODLE_SITENAME=New-Site
        # Moodle administrator's username
        - MOODLE_USERNAME=moodleuser
        # Moodle administrator's password (PLEASE_CHANGEME is a placeholder)
        - MOODLE_PASSWORD=PLEASE_CHANGEME
        # SMTP server host for sending Moodle emails
        - SMTP_HOST=smtp.gmail.com
        # SMTP server port
        - SMTP_PORT=587
        # SMTP server username for authentication
        - SMTP_USER=your_email@gmail.com
        # SMTP server password for authentication
        - SMTP_PASSWORD=your_password
        # SMTP protocol for email delivery (TLS in this case)
        - SMTP_PROTOCOL=tls
        # Moodle no-reply email address
        - MOODLE_MAIL_NOREPLY_ADDRESS=noreply@localhost
        # Moodle email prefix
        - MOODLE_MAIL_PREFIX=[moodle]
        ports:
        - "80:8080"
        volumes:
        # Moodle data directory
        - moodledata:/var/www/moodledata
        # Moodle web root directory
        - moodlehtml:/var/www/html
        depends_on:
        - postgres
        networks:
        - MOODLE-NETWORK

    networks:
    MOODLE-NETWORK:




