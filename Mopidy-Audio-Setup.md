
### Mopidy (Audio Server) on the Raspberry Pi 3

Mopidy is an extensible music server that plays music from local disk, Spotify, SoundCloud, Google Play Music, and more. There are many different user interfaces (web client, etc.) wich you can download and use to view, edit the playlist from any handheld device i.e. phone, tablet including a computer. Mopidy also allows the use of range of MPD (Older Music Player Daemon) client for which applications are available at the Apple and Andriod stores. Head off to https://www.mopidy.com to learn more about the Mopidy music server and what it has to offer.

There are many reasons i use Mopidy in comparison to the other music players available. The foremost being that it's Python based and has one of the most refreshing interfaces i could find. Secondly, Mopidy has a very vibrant community around it with some of the best support for plugins and interfaces that I could find. To top it all it would run on Raspbian on the Raspberry Pi which was important.

### Installing Mopidy on Raspbian

Let's step through the commands to download and install the base Mopidy player on your RaspberryPi.

* Make sure you have the "git" client installed on your machines. Most tutorials listed on this website require the use of git to download code from the authors [Github](https://github.com) repository. 
* If you do not have "git" installed please we will need to download and install git on Raspbian using `bash# sudo apt-get install git`. This will install the git client on your RaspberryPi. We will be using the git client to clone a lot of the repositories included in this tutorial.
  * Let's start by cloing the github repository for Mopidy from https://github.com/mopidy/mopidy using the following command - `bash# git clone https://github.com/mopidy/mopidy`
  * Once you've cloned the mopidy repository to your local machines we can proceed and compile mopidy locally on your Raspberry Pi.
  * Change into the downloaded Mopidy directory to build and install using the following commands, `bash# sudo python setup.py install`. This command will build and install mopidy. Make sure you are using `sudo` before the command because without superuser permissions you will not be able to install the binaries into the system path.
* Let's now go ahead and clone the github repository for Mopidy-AlsaMixer from [Github Mopidy AlsaMixer](https://github.com/mopidy/mopidy-alsamixer) using the following command `git clone https://github.com/mopidy/mopidy-alsamixer`
  * Let's now change into the downloaded mopidy-alsamixer directory to build and install the application. 
  * To build and install mopidy-mixer issue the following commands, `bash# sudo python setup.py install`. This should build and install mopidy-alsamixer onto the Raspberry Pi.

### Installing Dependencies 

Now that we have installed Mopidy lets review some of the other non-documented dependencies that we might consider installing. If we had not installed Mopidy from source [Github](https://github.com) and rather installed Mopidy using the Raspbian packages `bash# sudo apt-get install mopidy` the system would have auto resolved the dependencies. However, we've chosen not to install the stock packages since they are really outdated. We prefer the latest stable codebase from Github which is the reason why we are taking the pain to go about installing mopidy and it's dependencies the hard way. 

* Lets proceed now and manually install the following packages. These are part of the pre-requisites which i found missing and spent sometime/effort understanding what was required. The commands are - 
 `sudo apt-get install python-gst-1.0 gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-tools` and 
 `sudo apt-get install gir1.2-gstreamer-1.0 gir1.2-gst-plugins-base-1.0`

With the above step we have completed installation of mopidy and its key dependencies. There are still many plugins avaialble for mopidy which we can't cover in this tutorial. To download and install the relevant plugins (to play different types of audio files, streams, etc.) we would recommend that you visit the mopidy page and look up the documentation. Lets now proceed with configuration of our local mopidy setup on the Raspberry Pi.

### Modifying the Out Of The Box Mopidy Config File

* You will now need to open up your Mopidy configuration file at /etc/mopidy/mopidy.conf and edit it to suit your requirements. At the end of the installation you should be left with a default out of the box configuration for Mopidy which will need tweaking.
* For details on each of the configuration options please visit - [https://docs.mopidy.com/en/latest/config/](https://docs.mopidy.com/en/latest/config/). 
* Please including configuration for the Mopidy AlsaMixer module into /etc/mopidy/mopidy.conf file. You can refer to a sample config for the mopidy-alsamixer at [https://github.com/mopidy/mopidy-alsamixer](https://github.com/mopidy/mopidy-alsamixer)
* Now that we've got this far we'll need to add the local music repository to the configuration. Open up your mopidy configuration file and look for the `[local]` configuration section within it. The `[local]` configuration section is where you will add the location path to your local music store. This one needs to be configured with a simple local unix path based on the location of the files on your Raspberry Pi. 

It's time to review the configuration and get mopidy up and running so that we can listen to some music. 

### Starting Mopidy & Initilize Cache

* Start up Mopidy using `sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf`. It's likely that you will see errors when you first start mopidy. Work through the errors and resolve them one at a time. Work through the errors and make sure that you are able to get mopidy running without any errors on the Raspberry Pi.
* A best case outcome could be that the only error is that the local plugin configuration has not found any media files. This is a best case outcome and it might or might not be applicable to you.
* Run the following command to initiate creation of a local music cache. This assumes that you have followed all the instructions above, installed and configured mopidy, created the default configuration and are now ready to create the local music cache. Issue the following command, `sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf local scan`. This should run for a while depending on how much content you've got in your local music repository. I use my usb drive mounted on /mnt/usb0 and it took a while for Mopidy to scan through the content. 
* Once you've setup mopidy you should confirm if you are able to connect to the User Interface. Let's start mopidy with the command, `sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf`. 
* Let's now connect to the user interface via a web browser. This will be a local web site for you to please change the IP address to suit that of your Raspberry Pi `http://RaspberryPI_IP_Address_Here:6680/`.
* If you have the musicbox client installed you will see a link for it at the above page. Else you'll need to clone the git repository for Mopidy Musicbox Web client using the following command, `bash# git clone https://github.com/pimusicbox/mopidy-musicbox-webclient`.
  * Change into the downloaded mopidy-musicbox-webclient directory to build and install the webclient. Issue the following commands, `sudo python setup.py install`. This will build and install the mopidy-musicbox-webclient package onto the RaspberryPi.
  * Once you've installed mopidy music box webclient you should confirm if you are able to connect to the User Interface. 
  * Start mopidy with the command, `sudo /path/to/mopidy --config /etc/mopidy/mopidy.conf`.
  * Then connect to the user interface via a web browser  `http://RaspberryPI_IP_Address_Here:6680/musicbox_webclient/index.html`

### Configuring Mopidy With Additional Internet Radio Stations

If you've come this far and have follwed each of the instructions listed above you should have a working Mopidy installation on your Raspberry Pi. If you face errors we would recommend using google and also looking at the Mopidy forums to work through the issues. Your best company is google and lots of patience..:). If you are looking for audio streams to add to your local music repository you might want to check out these URL's - 

* [Internet-Radio.com](https://www.internet-radio.com/)
* [Australian Live Radio](http://www.australianliveradio.com/)
* [Listen Live](http://www.listenlive.eu/jazz.html)
* [Australian Broadcasting Corporation Radion Channels Online](https://radio.abc.net.au/help/streams)

Here are links to a few articles that talks about getting Mopidy up and running with different types of music streams - 

* [Mopidy with Spotify](http://raspberry-at-home.com/mopidy-spotify-client/)
* [Mopidy with Snapcast](https://home-assistant.io/blog/2016/02/18/multi-room-audio-with-snapcast/)
* [Raspberry Pi As An Internet Radio](https://baheyeldin.com/technology/linux/raspberry-pi-2-internet-radio-using-mopidy.html)

Obviously you might consider automating the startup of Mopidy. Like everything on unix/linux there's tons of ways of doing this. We would recommend that you could consider using daemon (daemontools) or simply /etc/rc.d/rc.local. Key in the startup command into rc.local and reboot the machine to find mopidy running in the background.

Enjoy listening to your music!!! Thank you!!!


