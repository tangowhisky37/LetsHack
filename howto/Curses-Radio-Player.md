
## Curses (Command Line) Based Python Radio Player

This short piece focuses on configuring your Raspberry Pi to launch radio stations using a curses based Python command line application. Curses allows for a menu based approach at the command line, think of it as the minimalist GUI at the console. 

* If you are anything like me you like to have everything running through a console or at-least launched directly from the console. If command line and curses isn't your thing and you prefer GUI for everything then this tutorial isn't for you. 
* It's just the flexibility of being able to manage simple processes and launch them via the console that makes working with curses and command line applications such a breeze.
* Also another advantage of working with GUI applications is that one does not have to worry about bloatware GUI applications that consume large amounts of resources when you can get similar stuff done for a fraction of the cost i.e. cost of memory/cpu consumption.
* That thought process also applies to all the music i like to hear including how i like to hear it. And the answer to that is a curses (Command Line or CLI) based audio and radio player. 
* There are many curses based audio players out there and if you are interested in looking at the options before making your mind up please visit - [TuxArena - Console Based Music Players](http://www.tuxarena.com/2011/12/10-console-music-players-for-linux/). In this short piece we will focus on getting a console based radio player up and running on your Raspberry Pi.

### What Is PyRadio

* PyRadio is a console based Internet radio player. You can read more about PyRadio here [http://www.coderholic.com/pyradio/](http://www.coderholic.com/pyradio/).
* PyRadio was written by Ben Dowling, a 29 year old British Software Engineer based in Mountain View, California. Ben loves writing code, learning, and launching new products.

![PyradioImage](https://raw.githubusercontent.com/tangowhisky37/RasPiSetupGuide/master/images/pyradio.jpg)

* PyRadio is implemented in Python, and uses mplayer for media playback. PyRadio has been tested under Ubuntu 9.04, but should run without any problems under most UNIX based operating systems. 
* I've been able to compile PyRadio on Rapbian on the Raspberry Pi 3, so you shouldn't have any issues getting it up and running on the Raspberry Pi. 

### Installing PyRadio

* To get it running you'll need Python and mplayer. Let's get started by installing mplayer.
  > `bash# sudo apt-get install mplayer`
* Once you have mplayer installed you are good to download, compile and install PyRadio. So let's go ahead and download PyRadio.
  > `bash# git clone https://github.com/coderholic/pyradio.git`
* With PyRadio downloaded, change into the directory and issue the following command to compile PyRadio.
  > `bash# sudo python setup.py install`
* With the above complete you should now have completed compiling and installing PyRadio on your Raspberry Pi. 

### Spinning Up PyRadio

* You should now be able to launch the application from the console. 
  > `bash# pyradio`
* Select your station from the list and hit enter. Look up the manual for information on other commands. Enter starts playing and Space stops playing. Ctrl+C exits from the player.
* You can add new stations to the list by editing the "stations.csv" file. If you have Python2.7 you'll find the stations.csv file at the following location - "/usr/local/lib/python2.7/dist-packages/pyradio-0.5.2-py2.7.egg/pyradio/stations.csv"
* If you are looking for additional stations that stream music of your choice head over to [Internet Radio](https://www.internet-radio.com), find your channel, copy the link for the PLS (Playlist) option (which if you click opens up a streaming music player on your desktop) and paste it into your stations.csv file. 
* When you copy the URL for the PLs (Playlist) from any website, just make sure to only keep the URL of the streaming service and delete the rest of the URL which is padded onto the URL.

Hope you've found the HowTo useful and have been able to get your own Python based curses music player up and running.

Enjoy!!!
