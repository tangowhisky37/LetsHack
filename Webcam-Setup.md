
### RPi Web Cam - RaspberryPi Web Cam (Raspberry Pi 3)

RPi Cam is a project that is geared at configuring your RaspberryPi for purposes of streaming video. This basically means you can use your Raspberry Pi as a smart Web Streaming solution. This article assumes that you have your onboard camera installed and configured. Going into the integration and configuration of the on-board Raspberry Pi camera is out of the scope of this article. If you are looking to setup and configure your configure your camera then we would recommend that you look at youtube. You will find that there are many nice tutorials geared towards walking users through the integration of the on-board camera with the Raspberry Pi board. 

To read more about the RPi Web Cam project head here - [Rpi Web Cam Project](http://elinux.org/RPi-Cam-Web-Interface). Let's get going with installation and configuration of our Raspberry Pi Web Cam.

* Make sure you've followed the online tutorials (Youtube, etc.) and have integrated and configured your Raspberry Pi Webcam.
* Once you've configured the on-board camera boot up the Raspberry Pi and open up a console. 
* At the bash prompt you will need to run, `bash# raspi-config`. At the menu that pop's up go into "Interfacing Options" and enable the camera option there. You will most likely be asked at the end to reboot your Raspberry Pi. Even if you are not asked to reboot your Raspberry Pi it's a good idea at this point to reboot the device.
* Once the Raspberry Pi comes back online we'll head over to the bash console again and focus on updating the packages on the Raspbian Linux Operating System to the latest packages. The steps for installation include - 
  * Let's make sure our distribution has all the latest packages. We'll upgrade using the following commands - 
  * To obtain your local repo issue the following command - `bash sudo apt-get update` 
  * Once the above step is complete issue the following command to upgrade all the relevant packages for which updates are now available, `bash# sudo apt-get upgrade`.  
  * The upgrade of the packages will take a while. You might be asked to answer "yes/no" for the installation to continue. Obviously, you'll answer "yes" where relevant.   
* Once the operating system package update has completed let's  go ahead and clone the repository required to install RasPi cam.
  * Clone the repo using the following command - `bash# git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git`
  * Change into the Rpi Webcam directory - `bash# cd RPi_Cam_Web_Interface`
  * Before we initiate the installation you want to make sure that all the relevant scripts are in executable status. Issue the following command for that - `bash# chmod u+x *.sh`
  * The installer will ask you a bunch of questions. Most importantly the location for the Raspicam web folder. We would recommend you create a separate folder in /var/www/ called "webcam", since Rpi Cam will copy a lot of content into that folder and you don't want it lying around in your document root i.e. /var/www.
  * Issue the following command to create the directory for Rpi Cam to install all the web content, `bash# mkdir /var/www/webcam`.
  * Now we are ready to get the installation going. Issue the following command at the bash prompt, `bash# ./install.sh`

Once the installation has completed head off to the Raspicam web foder through your web browser and you should be able to see your webcam in action. The installer should have made relevant entries into /etc/rc.local which will ensure that everytime your RaspberryPi boots up the RPi Web Cam server starts up automatically. 

The scripts to start and stop your webcam are in the Rpi Webcam directory. The commands you would use are - 

* Starting the webcam service - `bash# ./start.sh`
* Stopping the webcam service - `bash# ./stop.sh`

There are various other approaches to automating the startup of services like the RasPi Cam e.g. using daemontools, monit (monitoring daemon), custom startup scripts in /etc/rc.*d. See what works best for you. This article won't dive into the details of automating startup or shutdown of the Rpi Webcam service.

Thanks!!!

