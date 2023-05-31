+++
title = "Multi-Site Single Server"
description = "Procedural Workflows"
weight = 2
+++

{{< panel title="Tried & Tested Workflow" style="success" >}}

I have used this procedure to setup multiple websites on a single low-cost VPS using Dynamic Hosting with NGINX

{{< /panel >}}

# Debian VPS deployment workflow

## Simple Outline

* Purchase Domain name.
* Choose a reputable VPS provider.
* Select Debian as the operating system.
* Connect to the VPS via SSH.
* Install necessary packages.
* Configure HTTP server.
* Deploy your application.

## Purchase Domain Name

### 1. Simple as
   
## Rent Virtual Private Server (VPS)

### 1. Get a cheap VPS with IPV6 & IPV4 addressing
### 2. Get one with private networking
   
## Initial Server Setup

### 1. Setup Debian Server

### 2. Copy IPV4 address of server/host to A record of Domain name host

### 3. Copy IPV6 address of server/host to AAAA record of Domain name host

### 4. Alter CNAME record to include a redirect when WWW is excluded

### 5. Test this configuration by pinging the domain name. One should see the IP address for the host server

### 6. SSH login as ROOT user

### 7. Generate an SSH key pair with SSH-keygen (Locally)

### 8. Copy public key to server:

    ssh-copy-id -i ~/.ssh/id_rsa.pub root.domainname.com

### 9. On server:

    vim etc/ssh/ssh_config

### 10. Alter SSH Config file to express the following changes:
    
    PasswordAuthentication no
    UsePAM no
    ChallengeResponseAuthentication no

### 11. Reboot SSH:

    systemctl restart sshd

### 12. Update server

    apt update

### 13. Install software

    apt install nginx
    apt install certbot (for https)
    apt install python-certbot-nginx

### 14. Copy sites-available template to new site file/profile for NGINX

    cp /etc/nginx/sites-available/default /etc/nginx/sites-available/newsite

### 15. Edit this new site file/profile:

vim /etc/nginx/sites-available/newsite

    server {
        listen 80 ;
        listen [::]:80 ;

        root /var/www/newsite;

        index index.html index.htm index.nginx-debian.html;

        server_name newsite.com www.newsite.com;

        location / {
            try_files $uri $uri/ =404;
        }
    }

### 16. Symlink newsite to enabled

    ln -s /etc/nginx/sites-available/newsite /etc/nginx/sites-enabled/

### 17. Make a directory for site

    mkdir /var/www/cabin

### 18. write/upload test index.html file

    vim index.html...

### 19. Reboot NGINX

    systemctl reload nginx

### 20. Get HTTPS cert from certbot

    certbot --nginx

    enter email

### 21. Agree to terms.
    
### 22. Disagree to sharing email.
    
### 23. Choose what site address get certs.
    
### 24. Yes to redirecting HTTP to HTTPS.
    
### 25. Type in domain and check/confirm setup of nginx and certbot.
    
### 26. Set up a cron job to renew check and renew certbot monthly

    root@newsite:/var/www/newsite crontab -e

    1 1 1 * * certbot renew

## Deploy

### 1. Generate the HUGO static output into public folder

    HUGO

### 2. Copy local static public folder to /var/www/newsite
### 3. NGINX should spot the change and update the site immediately