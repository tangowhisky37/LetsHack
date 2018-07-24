
## Configuring the Raspberry Pi 3

This tutorial provides a view of the various key Raspberry Pi (on Raspbian) setup commands that i end up using when setting up a new Raspberry Pi. This tutorial is intended to serve more as a reference document for future builds with the hope that others might also find it useful. This document will evolve over a period of time so the structure / flow might not necessarily make a lot of sense to the reader. Drop me a note if you have any questions. 

This tutorial refers mainly to Raspbian (Jesse, Stretch) on the Raspberry Pi 3. Other versions of Linux i.e. other than Raspbian, could need other approaches for configuration. 

### Configuring a wireless adapter for the Raspberry Pi 3 (from a Windows desktop) on Raspbian before bootup

This section will focus on configuration of the wireless network adapter on the Raspberry Pi 3 when using Raspbian. This section assumes that you have downloaded the latest Raspbian image from [Raspberry Pi Website](http://www.raspberrypi.org) and burnt that image to your SD card. We won't go into the details of downloading the latest Raspbian Linux image and burning it to the Raspberry Pi. If you would like to read more about the different operating system options available for the Raspberry Pi please visit the [Raspberry Pi Website / Download section](https://www.raspberrypi.org/downloads/). We will also assume that you are using Microsoft Windows as your desktop, please see alternate tutorials if you are using Linux or a Mac as your desktop since the instructions will vary a bit. 

* Once you have burnt the image onto your SD card, pop it into the laptop. Your Microsoft Windows laptop should now detect the SD card as having two drives. 
* It will be able to mount the first drive called "boot" however it will complain about not be able to read the second drive and will ask you if you want to format the second drive. 
* Please be careful and answer NO, you do not want to re-format the second drive since it's been written with a filesystem that can be read by the Linux Kernel and hosts the Rasbian Linux Operating System. 
* Next we will create a file on the Raspbian boot partition and enter in relevant configuration details which will ensure that the Raspberry Pi once booted up, connects to the right wireless network.
* Open up windows explorer and let's access the "boot" drive which is one of the two drives that would have shown up on your Microsoft Windows desktop after you inserted the newly formatted SD card with Rasbian Linux into your desktop. 
* We would recommend that you use a command line based text editor avaiable through the CYGWIN toolset for windows to work on the text file. Personally i make use of the GIT Console for Windows which has a nice little command line interface with some of the basic text editing tools (VI, etc.) that one needs. 
* Let's create a file called "wpa_supplicant.conf" into which we'll be making a few entries - 

For Raspbian Jesse - 

> `network={`
> `   ssid="YOUR_NETWORK_NAME"`
> `   psk="YOUR_PASSWORD"`
> `   key_mgmt=WPA-PSK`
> `}`

For Raspbian Stretch - 

> `ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev`
> `network={`
> `   ssid="YOUR_NETWORK_NAME"`
> `   psk="YOUR_PASSWORD"`
> `   key_mgmt=WPA-PSK`
> `}`

Replace the SSID with your wireless network name and psk with your password. Then insert the SD card into the Raspberry Pi and boot it up. The Raspberry Pi should boot up and log you into the graphical desktop. 

### Configuring Raspbian on the Raspberry Pi 3 (from your Windows Desktop) to bootup with SSH enabled 

This section will focus on enabling the SSH (Secure Socket Shell) server on the Raspberry Pi 3 when using Raspbian before the Raspberry Pi has been booted up. This section assumes that you have downloaded the latest Raspbian image from [Raspberry Pi Website](http://www.raspberrypi.org) and burnt that image to your SD card. We won't go into the details of downloading the latest Raspbian Linux image and burning it to the Raspberry Pi. If you would like to read more about the different operating system options available for the Raspberry Pi please visit the [Raspberry Pi Website / Download section](https://www.raspberrypi.org/downloads/). We will also assume that you are using Microsoft Windows as your desktop, please see alternate tutorials if you are using Linux or a Mac as your desktop since the instructions will vary a bit. 

Please also read through the section above to understand how to configure the wireless adapter on Raspbian (Jesse, Stretch) on the Raspberry Pi 3 to connect to your local wireless network.

* Once you have burnt the image onto your SD card, pop it into the laptop. Your Microsoft Windows laptop should now detect the SD card as having two drives. 
* It will be able to mount the first drive called "boot" however it will complain about not be able to read the second drive and will ask you if you want to format the second drive. 
* Please be careful and answer NO, you do not want to re-format the second drive since it's been written with a filesystem that can be read by the Linux Kernel and hosts the Rasbian Linux Operating System. 
* Next we will create a file on the Raspbian boot partition and enter in relevant configuration details which will ensure that the SSH service starts everytime the Raspberry Pi 3 boots up.
* Open up windows explorer and let's access the "boot" drive which is one of the two drives that would have shown up on your Microsoft Windows desktop after you inserted the newly formatted SD card with Rasbian Linux into your desktop. 
* We would recommend that you use a command line based text editor avaiable through the CYGWIN toolset for windows to work on the text file. Personally i make use of the GIT Console for Windows which has a nice little command line interface with some of the basic text editing tools (VI, etc.) that one needs. 
* From your command line text editor let's create an empty file called "touch.

> `touch ssh`

* Note that you have created an empty file with the name ssh and no file name extensions. If you tried doing this from your windows text editor you could run into issues because windows (unlike Unix, Linux) likes to have files with file extensions i.e. .docx, .txt, .exe, etc. 
* So working from within the GIT shell for windows or CYGWIN is your best best

Then insert the SD card into the Raspberry Pi and boot it up. The Raspberry Pi should boot up and log you into the graphical desktop. You should now be able to access the Raspberry Pi over the network

### 5 Inch LCD on your Rasbperry Pi 3

If you are in the market for an affordable 5 inch touch screen then you might want to consider the following option from Banggood - [5 Inch TFT LCD Touch Screen With Case](https://www.banggood.com/5-Inch-HDMI-TFT-LCD-Touch-Screen-For-Raspberry-PI-With-Case-p-977666.html). I purchased this to add to my IoT setup at home and have been very pleased with the results. The case is really flimsy and you might want to replace it with an alternate 3D printed case but it mostly gets the job done.

* The setup at home incldues a Rasbperry Pi 3 within the enclosure connected to the TFT LCF touch screen. 
* The entire unit is mounted on a wooden cabinet in the dining room using Velcro. 
* The Velcro I purchased can support upto 3Kgs and the total weight of the enclosure and screen one is not more than a 250-300 grams. 
* I run Firefox ESR as the browser on the touchscreen to control lighting in the house. 
* My IoT setup at home is based on [OpenHAB](www.openhab.org). OpenHAB is the IoT platform running on another Raspberry Pi 3 at home.
* The OpenHAB setup is configured to integrate all the different (Philips Hue, RF433 Mhz, SonoFF, ZWave, etc.) IOT technologies I've hacked with over the years. 

The drivers for the TFT LCD can be downloaded from - [Spot Pear](http://www.spotpear.com/learn/EN/raspberry-pi/Raspberry-Pi-LCD/Drive-the-LCD.html). The documentation as with most ali-express and banggood items is really poor but is simple enough for someone with fundamental linux/unix skills to work through.

Happy hacking!!! Thank you!!!

