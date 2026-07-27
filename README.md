# ***THIS PROJECT IS CURRENTLY IN PROGRESS - PLEASE DON'T USE IT YET.***

![](imgs/host.png)
## This is a tutorial on how to host your own website on a Raspberry Pi by using your own domain.
Did you ever asked yourself how to host a website without having to pay those expensives hosts and try to spend as less money as possible, without having to keep your computer on all day to host a website? \
If yes, then this page is for you.
## Table of contents:
[1. What will you learn from this?](#1-what-will-you-learn-from-this)\
[2. FAQ](#2-faq)\
[3. Requirements](#3-requirements)\
[4. Installation - Ubuntu OS on Raspberry Pi](#4-installation---ubuntu-os-on-raspberry-pi)\
[5. Minor Tweaks - Desktop OS Only](#5-minor-tweaks---dekstop-os-only)\
[6.Installing NGINX](#6-installing-nginx)\
[7. Control Panel Installation.](#7-control-panel-installation.)\


## 1. What will you learn from this? 
- How to install Ubuntu on SSD by using SATA to USB3 Adapter.
- Install NGINX on your Raspberry PI.
- Install a control panel for your website.
- How to point your Domain to your Raspberry Pi IP.
- How to make your website public through port forwarding.
- Secure both your website and your control panel with firewalls and protection.
- Automate emergency notifications. If something happens with your host, panel, etc, you will get a notification on your phone via Telegram, Discord, Email, etc.

## 2. FAQ:
```
Why can't I use an SD Card like all Pi users do? 
```
Switching a Raspberry Pi from a microSD card to an SSD massively boosts read/write speeds, improves long-term reliability, and prevents data corruption during unexpected power loss. In other words, your SD Card may always corrupt unexpectedly and makes you lose all your work, and it's slower.

```
Is it worth it?
```
If you don't want to spend 10£/month for a basic web host, yes. Unlike normal hosting, where you pay 10£/month for ONE website, with Raspberry Pi and NGINX you can host multiple websites without paying anything. (except for domains)

```
Do I need to know linux commands?
```
Not necessarily. I highly recommend you learn ubuntu terminal commands for long-term education. Linux is a must-know skill that every developer should touch at some point. You can't do anything on your computer if you don't even know how to turn it on, right?



## 3. Requirements:
- A computer with internet access (can be both laptop and desktop).
- A Raspberry Pi (preferably 4+. Anything under Pi 4 will have issues with SSDs).
- SATA to USB3 Adapter.
- Raspberry Pi Power Supply.
- SSD (250+GB Recommended for long-term scalability).
- SD Card (4GB+) - We won't need this for long.
- SD Card to USB Adapter. There are many choices and models online, they are all the same, as long as they do the job.
- Raspberry Pi 7" Touchscreen (optional, totally not needed for our project but useful if you want to have a weather station, Home Assistant Implementations etc.)
![requirements image](imgs/requirements.png)

## 4. Installation - Ubuntu OS on Raspberry Pi.
To install Ubuntu on your Raspberry Pi you will need:
- Raspberry Pi Imager. [Download from Official Website](https://www.raspberrypi.com/software/)
- SATA to USB3 Adapter.
- SSD (250GB+ Recommended for scalability and huge websites with lots of images).

__INSTALLATION STEPS__
1. Download Raspberry Pi imager.
2. Install it.
3. Connect your SD Card to your computer.\
>In my case, the SD Card is mounted on (J:)\
![Raspberry PI Imager](imgs/sd.jpeg)
4. Open Raspberry Pi Imager. \
You will now see this: 
![Raspberry PI Imager](imgs/imager.png)
> If you see random characters like mine (? NNMNROMLQ), just ignore them. I don't know why it looks like that, it might be from my side only.
5. Choose your device. In my case, I am using a Raspberry Pi 4, so I will chose the second option. 
6. Click Next (or LCVR in my case - don't ask, I dont know why it looks like this.)\
![Raspberry PI Imager](imgs/imager2.png)
7. In the OS menu, we have to install a bootloader on the SD Card first. Scroll down until you find ***MISC UTILITY IMAGES*** and click on it. It should take you to the next section. If it doesn't, just click ***NEXT***\
![Raspberry PI Imager](imgs/imgr3.png)
8. Select ***Bootloader (Pi 4 Family)***.
>It might say something else depending on the Pi you're using.\
![Raspberry PI Imager](imgs/imgr4.png)
9. Select ***Select USB Boot*** and click next.
![Raspberry PI Imager](imgs/imgr4-1.png)

10. Select the SD Card you have connected to your PC in ***step 3***, and click next.
>Since mine is in J: and it's a 32gb SD Card, I will select the second option.\
![Raspberry PI Imager](imgs/imgr5.png)
11. Double check the details and make sure they match, and click next. ***You must make sure the Operating system is USB BOOT***.\
![Raspberry PI Imager](imgs/imgr7.png)
12. Make sure you understand that **once you write the image, everything will be erased on that SD Card**, and click the red button.\
![Raspberry PI Imager](imgs/imgr8.png)

13. Wait for the Imager to write the image on the SD Card.
14. Once completed, you will see this screen. Click on the red button to close the app and **eject the SD Card**.\
![Raspberry PI Imager](imgs/imgr9.png)

15. Insert the SD Card into your Raspberry Pi.\
![Raspberry PI SD Location](https://www.raspberrypi.com/documentation/computers/images/peripherals/sd-card.png?hash=55bfa3fdcf4c6131e843b4a9f5656a2e)
16. Power on your Raspberry Pi by plugging the power cable in the USB C Power Supply.\
![Raspberry PI SD Location](https://ofmarginalinterest.wordpress.com/wp-content/uploads/2022/06/pipower.jpg)
17. Once the Pi has been turned on, it will now copy the bootloader code into the Raspberry Pi. **Keep an eye on the green LED**. Once it's finished you will see the green LED flashing continuously. 
On the other hand, if you have a screen connected to your Raspberry Pi via HDMI, you will see a green screen. That is totally normal. On the following image, the green LED is marked as "ACT".\
![Raspberry Pi Board LED ](imgs/pi1.png)
18. Once the green LED starts flashing, you can now unplug the power supply from the Raspberry Pi. ***Make sure you unplug the power cable, and NOT the SD Card.***
19. Only after powering off, you can now safely remove the SD Card. We won't need it anymore.
20. Connect your SSD to your PC using the SATA to USB3 adapter.
![Raspberry Pi Board LED ](imgs/ssd.jpeg)
>If you are getting a message to format the SSD, don't worry about it, you can ignore it. The Pi Imager software will format it anyway.
21. Open **Raspberry PI Imager**.
22. Select your Pi Model once again and click **next** (Again, my Pi is *Raspberry Pi 4*).
![Raspberry PI Imager](imgs/imgr10.png)
23. Select the desired OS. **Since I am using a monitor for my Raspberry Pi 4, I will install the Desktop version (64-Bits).** If you're planning to use a monitor, it can be a simple HDMI monitor or a Pi touchscreen.
24. After selecting your desired OS, click next.
![Raspberry PI Imager](imgs/imgr11.png)
25. Select your SSD from the Storage menu and click Next. **In my case, I am using a KINGSTON SSD**. Your device name will most likely be different. 
![Raspberry PI Imager](imgs/imgr12.png)
26. **Customisation: Choose Hostname -** Choose the desired hostname for the Raspberry Pi and click Next. *This can be any name you wish, but make sure to remember it. **We will later use this hostname to connect via ssh** and see it in our internet router.*
![Raspberry PI Imager](imgs/imgr13.png)
27. **Customisation: Localisation -** Set your Localisation and click next. This is used to set the time zone and keyboard layour for your Raspberry Pi. *In my case, I will use London as Capital City, Europe/London Time zone and GB Keyboard Layout as I live in UK.*
![Raspberry PI Imager](imgs/imgr14.png)
28. **Customisation: Choose Username -** Set your username and password for your Raspberry Pi and click **Next**. This will be used to log into your OS (just like in Windows). *Make sure you remember the password.*
![Raspberry PI Imager](imgs/imgr15.png)
29. **Customisation: Choose Wi-Fi -** Enter your Wi-Fi SSID and Password and click **Next**. This will connect your Raspberry Pi to your Wi-Fi. 
![Raspberry PI Imager](imgs/imgr16.png)
30. **Customisation: SSH Authentication -** Enable your SSH Autenthication and click **Next**. This will allow us to connect to our Raspberry Pi remotely. *I recommend using the **Use password authentication** for easier access.* 
![Raspberry PI Imager](imgs/imgr17.png)
31. **Customisation: Raspberry Pi Connect -** IF YOU ARE USING A MONITOR, I recommend using the Raspberry Pi Connect to connect to your Pi and control the desktop remotely. If you don't have a Desktop OS, you can skip this step. 
![Raspberry PI Imager](imgs/imgr18.png)
>NOTE: You will need to create an account on the Raspberry Pi website in order to receive an Authentication Token.
32. **Write Image -** Review all the settings and click **Next**. This will now write the image on the connected SSD.  
![Raspberry PI Imager](imgs/imgr19.png)
33. Wait for the installation. This should take a minute or two. *Grab a coffee, we'll be here for longer..*
![Raspberry PI Imager](imgs/imgr20.png)
34. Once finished, click on the **Finish** red button (or whatever it says.)
![Raspberry PI Imager](imgs/imgr21.png)
35. Remove the SSD from the Computer. 
36. **Make sure the Raspberry Pi has no SD card inside and it's completely powered off.**
37. Connect the SDD to the Raspberry Pi via SATA to USB3 adapter into a USB3 Port **(blue USB)**
![PI USB PORT](imgs/pi2.png)
38. Power the Pi by inserting the USB-C cable into the USB-C power port. ***(Check the image on Step 16)***
39. Wait for the Pi to Boot. If you're using a screen, you will see when it finishes booting. If not, just wait a minute. 
![PI USB PORT](imgs/pi3.png)

**CONGRATULATIONS!**\
You have successfully installed an OS on your SSD and connected it to your raspberry pi!\
However, there are still some tweaks we have to do in order to be happy with our Pi. 

## 5. Minor Tweaks - Dekstop OS ONLY.
If you've noticed, your monitor will most likely be upside down.\
You can use your finger to manually rotate the screen. All you have to do is:
1. Open the Activities overview and type Displays.
2. Click Displays to open the panel.
3. Select your target display in the preview area.
4. Click Orientation and choose your preferred setting:\
-Landscape (Normal)\
-Portrait Left (90 degrees counter-clockwise)\
-Portrait Right (90 degrees clockwise)\
-Landscape (flipped) (180 degrees upside down)\
5. Click Apply and select Keep Changes.

Otherwise, you can connect to your Raspberry Pi by using *Raspberry Pi Connect*.\
1. Head to [Raspberry Pi Connect Official Website](https://www.raspberrypi.com/software/connect/).
2. Create an account or Login. 
3. Once you managed to create your account or login, you should see your device in the following menu.\
Click on **Connect Via** and select **Screen Sharing**.
![PI Connection](imgs/picon.png)
4. A new browser window will open and you will be connected to your Raspberry Pi. Now you can control it like a normal computer. 
5. Head over to **Pi Icon > Preferences > Control Centre**
![PI Connection](imgs/picon2.png)
6. On the left side, scroll down until you find **"Screens"**. Select your monitor (it should be **DSI-1**) > **Orientation** > Click on **Inverted** and finally click on **Apply**. 
![PI Connection](imgs/picon3.png)
7. The screen will now look normal again.
>If your mouse is now inverted in the Browser Page, it's totally normal. We'll get it fixed in the next step.
8. Close the browser page. 

**Congratulations! Now your monitor is not inverted anymore!**

## 6. Installing NGINX.
From this point forward, we'll work on SSH from our personal computer. 
I am using [WSL - Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) on my Windows 11 machine. This allows me to have Ubuntu freedom and power directly on my personal machine without having to dual-boot.\
**If my pictures look different from your terminal, is because I have modified my terminal to look better. Don't worry, this doesn't change any commands we'll use.**

1. Open *Command Prompt* **or** *Terminal* on our PC.  
2. Connect to our Pi by using ***SSH***. In my case, my username and host is *pi@pi*, but yours will be the same ones you have set up during steps **26, 28**.
![PI ssh connection](imgs/cmd.png)
When asked if you want to continue, type "yes" and press **enter**.
3. Enter the password **you have set up for your pi** and press **enter**.
![PI ssh connection](imgs/cmd2.png)
>Note: You won't see your password when you're typing it. It's completely normal. 
4. Notice the terminal is now showing us as *user@host*. That means we are now connected to the Pi and controlling it. __We are no longer in Windows Command Prompt, but we are in Ubuntu!__. 
![PI ssh connection](imgs/cmd3.png)
5. Time to update our OS. Type the following commands and press **enter** after each command. **Enter the password if prompted**.
```
sudo apt update
sudo apt upgrade
```
![PI ssh connection](imgs/cmd4.png)
>If asked if Continue, type "Y" and press enter. 
The OS is now getting updated. Wait until it finishes. This is the equivalent of updating your Windows.
![PI ssh connection](imgs/cmd5.png)

6. To install NGINX, type the following commands and press **Enter** (**Remember to type "Y" and press enter if asked to continue**)
```
sudo apt install nginx
```

![PI ssh connection](imgs/cmd6.png)
7. Check your NGINX is up and running. Type the following command. You should see a similar output like in my picture.  
```
systemctl status nginx
```
![PI ssh connection](imgs/cmd7.png)
8. Press **CTRL+C** to leave the NGINX output. 
9. To test your own NGINX page, you first need to get your own public IP. If you don't know it, use the following command.
```
curl -4 icanhazip.com
``` 
![PI ssh connection](imgs/cmd8.png)
>It will return your public IP. You can now copy and paste that IP into your browser’s address bar: 
```
http://your_server_ip
```
You should now see a page that looks like this:
![NGINX Result](https://ubuntucommunity.s3.us-east-2.amazonaws.com/optimized/2X/7/7504d83a9fe8c09d861b2f7c49e144ac773f0c0d_2_800x334.png)

***Congratulations!*** You are now hosting your own website! However, we don't want people to look for our website by using an IP adress, right? In this case, get ready for the next step.

## 7. Control Panel Installation.