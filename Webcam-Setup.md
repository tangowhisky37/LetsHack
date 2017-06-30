
### RPi Web Cam - RaspberryPi Web Cam (Raspberry Pi 3)

- RPi Cam is a project that allows you to use your RaspberryPi for purposes of streaming video. This assumes that you have your onboard camera installed and cabling sorted. You can find details of the project here - [Rpi Web Cam Project](http://elinux.org/RPi-Cam-Web-Interface)

- Please make sure you have run "raspi-config" and enabled the camera option there. 
- The steps for installation include - 
  - Let's make sure our distribution has all the latest packages. We'll upgrade using the following commands - 
  - `sudo apt-get update`  <-- This updates the local repository
  - `sudo apt-get upgrade` <-- This upgrade all the relevant packages
- Once the above has completed let's  go ahead, clone the repository and install RasPi cam
  - `git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git`
  - `cd RPi_Cam_Web_Interface`
  - `chmod u+x *.sh`
  - `./install.sh`
- The installer will ask you a bunch of questions. Most importantly the location for the Raspicam web folder. 

Once the installation has completed head off to the Raspicam web foder through your web browser and you should be able to see your webcam in action. The installer should have made relevant entries into /etc/rc.local which will ensure that everytime your RaspberryPi boots up the RPi Web Cam server starts up automatically. 

There are various other approaches to automating the startup of services like the RasPi Cam e.g. using daemontools, monit (monitoring daemon), custom startup scripts in /etc/rc.*d. See what works best for you.

Thanks!!!

