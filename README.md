# This is a tutorial on how to host your own website on a Raspberry Pi.
Did you always wanted to have your own website but couldn't be bothered to pay those hosts?
You saw a cPanel at some point and you said "_wow, that makes life so much easier, I want one to control my website!_"
If yes, then this page is for you. 

## What will I learn from this? 
1. Install NGINX on your Raspberry PI
2. Install a control panel for your website. 
3. How to point your Domain to your Raspberry Pi IP.
4. How to make your website public through port forwarding.
5. Secure both your website and your control panel with firewalls and protection.
6. Automate emergency notifications. If something happens with your host, panel, etc, you will get a notification on your phone via Telegram, Discord, Email, etc.

## Requirements:
1. A Raspberry Pi.
2. Continuous internet connection.
3. A static IP.
4. Patience.

### NGINX - Installation
What is NGINX? 
> NGINX is a popular open-source software used as a web server, reverse proxy, load balancer, and content cache. It is widely used because it handles massive amounts of simultaneous web traffic quickly while using very little computer memory. 
#### Installing NGINX
To install NGINX, use the folling command on your Raspberry PI:
```
sudo apt update
sudo apt install nginx
```
