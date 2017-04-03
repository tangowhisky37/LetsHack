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

RPi Web Cam 
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

Thanks!!!
