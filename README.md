The installation guides below have mostly been written to serve as a reminder for the various systems administration tasks I usually perform when i pick up a new Raspberry Pi. However i believe these would also be useful to some of you out there who might stumble across simliar issues with your own Raspberry Pi's. 

Mopidy (Audio Server) on the Raspberry Pi 3

- Mopidy is an extensible music server that plays music from local disk, Spotify, SoundCloud, Google Play Music, and more. You edit the playlist from any phone, tablet, or computer using a range of MPD and web clients. Head off to https://www.mopidy.com to learn more about the Mopidy music server.
- Let's step through the commands to download and install the base Mopidy player on your RaspberryPi
  - Download and install git on Raspbian using "sudo apt-get install git". This will install the git client on your RaspberryPi. You will need the git client to clone a lot of the repositories included in this tutorial.
  - Clone the github repository for Mopidy from https://github.com/mopidy/mopidy using "git clone https://github.com/mopidy/mopidy"
  - Change into downloaded Mopidy directory to build and install using the following commands, "sudo python setup.py install". This should build and install mopidy.
  - Clone the github repository for Mopidy-AlsaMixer from https://github.com/mopidy/mopidy-alsamixer using "git clone https://github.com/mopidy/mopidy-alsamixer"
  - Change into the downloaded mopidy-alsamixer directory to build and install using the following commands, "sudo python setup.py install". This should build and install mopidy-alsamixer.
- Now that we have installed Mopidy we need to review some of the other non-documented dependencies we will need to install. If we had not installed Mopidy from source (github) and rather installed Mopidy using the Raspbian packages (sudo apt-get install mopidy) the system would have auto resolved the dependencies.
- However, we've chosen not to install the stock packages since they are really outdated. We prefer the latest stable codebase from Github.
- Lets proceed now and manually install the following packages. These are part of the pre-requisites which i found missing and spent sometime/effort understanding what was required. The commands are - 
  - sudo apt-get install python-gst-1.0 gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-tools
  - sudo apt-get install gir1.2-gstreamer-1.0 gir1.2-gst-plugins-base-1.0
- You will now need to open up your Mopidy configuration file at /etc/mopidy/mopidy.conf and edit it to suit your requirements. For details on each of the configuration options please visit - https://docs.mopidy.com/en/latest/config/
- Please including configuration for the Mopidy AlsaMixer module into /etc/mopidy/mopidy.conf file. You can refer to a sample config at https://github.com/mopidy/mopidy-alsamixer
- Now that we've got this far we'll need to add the local repository to the configuration. See your [local] configuration section and add the location path to your music store. This one needs to be configured with a simple local unix path. 
- Start up Mopidy using "sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf" and you should review the errors on the screen. Work through the errors. 
- Best case outcome would be that the only error is that the local plugin configuration has not found any files. Run the following command to initiate creation of a local cache, "sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf local scan". This should run for a while depending on how much content you've got in your local music repository. I use my usb drive mounted on /mnt/usb0 and it took a while for Mopidy to scan through the content. 
- Once you've setup mopidy you should confirm if you are able to connect to the User Interface. Start mopidy with the command, "sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf". Then connect to the user interface via a web browser  http://RaspberryPI_IP_Address_Here:6680/
- If you have the musicbox client installed you will see a link for it at the above page. Else you'll need to clone the git repository for Mopidy Musicbox Web client using "git clone https://github.com/pimusicbox/mopidy-musicbox-webclient"
  - Change into the downloaded mopidy-musicbox directory to build and install using the following commands, "sudo python setup.py install". This will build and install the mopidy-musicbox package onto the RaspberryPi.
  - Once you've installed mopidy music box you should confirm if you are able to connect to the User Interface. 
  - Start mopidy with the command, "sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf".
  - Then connect to the user interface via a web browser  http://RaspberryPI_IP_Address_Here:6680/musicbox_webclient/index.html
- Check out these URL's if you are looking for Audio Streams to add to Musicbox
  - https://www.internet-radio.com/ 
  - http://www.australianliveradio.com/
  - http://www.listenlive.eu/jazz.html 
  - https://radio.abc.net.au/help/streams
- Obviously you might consider automating the startup of Mopidy. Like everything on unix/linux there's tons of ways of doing this. You could consider using daemon (daemontools) or simply /etc/rc.d/rc.local. Key in the startup command into rc.local and reboot the machine to find mopidy running in the background.
- Enjoy listening to your music!!!

RPi Web Cam - RaspberryPi Web Cam (Raspberry Pi 3)
- RPi Cam is a project that allows you to use your RaspberryPi for purposes of streaming video. This assumes that you have your onboard camera installed and cabling sorted. You can find details of the project here - http://elinux.org/RPi-Cam-Web-Interface
- Please make sure you have run "raspi-config" and enabled the camera option there. 
- The steps for installation include - 
  - Let's make sure our distribution has all the latest packages. We'll upgrade using the following commands - 
  - sudo apt-get update  <-- This updates the local repository
  - sudo apt-get upgrade <-- This upgrade all the relevant packages
- Once the above have completed let's clone the repository and install RasPi cam
  - git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git
  - cd RPi_Cam_Web_Interface
  - chmod u+x *.sh
  - ./install.sh
- The installer will ask you a bunch of questions. Most importantly the location for the Raspicam web folder. 
- Once the installation has completed head off to the Raspicam web foder through your web browser and you should be able to see your webcam in action.
- The installer should have made relevant entries into /etc/rc.local which will ensure that everytime your RaspberryPi boots up the RPi Web Cam server starts up automatically. There are various other approaches to automating the startup of services like the RasPi Cam e.g. using daemontools, monit (monitoring daemon), custom startup scripts in /etc/rc.*d. 
- See what works best for you.

Hacking the Disk Layout on a Raspberry Pi Model A 
- Update (180517) - 
  - I've been doing a bit of reading and realized that after all re-partitioning might not be really required to increase SWAP
  - On the Raspberry Pi one can edit /etc/dphys-swapfile and set the swap file size
  - Then initilize SWAP using "sudo dphys-swapfile setup"
  - Once initialization is complete start SWAP using "sudo dphys-swapfile swapon" and "sudo dphys-swapfile swapoff" to run off SWAP.
  - Some sites suggests setting up SWAP or large amounts of SWAP is not a good idea since it reduces the life of the SD CARD. 
- This guide was put together while i was assembling 4 Raspberry Pi's for the local Raspberry Pi Hackers group i run. 
- I've had some challenges building the Raspberry Pi A. I used the stock Raspbian distro on a 8 GB SDHC card. The default file system is around ~4GB in size with SWAP around ~128 MB in size.
- The updates ran really slow and i couldn't get any software loaded on it. So I decided to re-do the partitions and throw in some additinoal swap space. The memory on the device was 128MB with SWAP as 128 MB created part of the default install.
- The steps to extending the file system and creating a new one are as follows - 
  - Backup your system in case of a mistake!
  - Use "fdisk /dev/mmcblk0" to view your partitions. Note down the start and end sectors for your main partition.
  - Make sure you have cross checked and double cross checked the sector start/end information.
  - use fdisk to delete the partition, but do not reboot.
  - Recreate a new partition (similar type i.e. ext4 Linux) but with a larger size starting at the same location as the previous one. I extended mine by another 2 GB to give me a total of 6 GB.
  - Create a new SWAP file system. I gave mine ~1GB of space. 
  - Reboot to activate the partition changes. You should check "fdisk -l" to see the changes.
  - On rebooting use "resize2fs /dev/mmclk0p2" to enlarge the root Linux file system.
  - Some sites recommended using, "e2fsck -f /dev/mmcblk0p2" to perform a file system check. This however didn't work for me hence i used the next step.
  - If you perform the following, "touch /forcefsck" you will force an fsck at every boot. Just make sure you have the following entry in your /etc/fstab, "/dev/mmcblk0p2	/  ext4	defaults, noatime	0	1"
  - Create the new SWAP file system by using, "mkswap /dev/mmcblk0p3". 
  - Configure the /etc/fstab file with the following, "/dev/mmcblk0p3	swap	swap	defaults	0	0"
  - Reboot and you should see SWAP auto mounted. 
  - Links to read - 
    - https://www.raspberrypi.org/forums/viewtopic.php?f=51&t=45265
    - https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=86536
    - https://www.raspberrypi.org/forums/viewtopic.php?t=15870&p=884216

Miscellaneous 
- When setting up the Raspberry Pi always upgrade Node Red using the script provided, "bash <(curl -sL https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/update-nodejs-and-nodered)" 
- Details on the manual upgrade are provided at - http://nodered.org/docs/hardware/raspberrypi 

Thanks!!!

Coming soon - 
- Setting up a USB Web Camera on Raspberry Pi 3
- Setting up your RaspberryPi 3 to able to VNC (remote connection) to the main display
- Mounting an external Windows recoginzed USB Device (& File System) on the RaspberryPi 3
- Changing the default sound output on the Raspberry Pi 3
- Installing and testing a USB mike on the Raspberry Pi 3


