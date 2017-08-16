## Stream Video & Control Your Robot via Your Web Browser 
### This project is aimed at building a Robot that allows for streaming of video and control from a web browser

* Here are some pictures of what you will end up with. This project has been built upon the Dexter Industries GoPiGo robot.
* Dexter Industries offers a modular robot with excellent video, printed tutorials to getting you up and running in a few hours. 
* The initial Dexter Industries robots were based on the Rapsberry Pi 2 (which is what my robot is based upon) but have now upgraded their robot package to support the Raspberry Pi 3.
* You can read more about this robot and pick your up from [Dexter Industries](http://www.dexterindustries.com)
* A lot of the code and functions included here are leveraged from Dexter Industries examples which are licensed under GPL.

![Mobile control of the GoPiGo Raspberry Pi Robot](https://raw.githubusercontent.com/DexterInd/GoPiGo/master/Software/Python/Examples/Browser_Streaming_Robot/Raspberry_Pi_Camera_controlled-by-mobile-browser.jpg "Control of the GoPiGo Raspberry Pi Robot with a mobile phone.")

![Robot Control and streaming through the browser](https://raw.githubusercontent.com/DexterInd/GoPiGo/master/Software/Python/Examples/Browser_Streaming_Robot/Raspberry_Pi_Camera_streaming-to-computer-browser.jpg "Streaming video through the browser of the GoPiGo")

![Controlling the GoPiGo robot with a mobile phone](https://raw.githubusercontent.com/DexterInd/GoPiGo/master/Software/Python/Examples/Browser_Streaming_Robot/Raspberry_Pi_Camera_controlled-by-mobile-browser.jpg "Streaming video from your Raspberry Pi Robot to your mobile phone.")

### Clone The Git Repository
* To start we need to clone the python project repository which will give us access to the code we need. 
* We can then work on resolving a bunch of depedencies and install some software. So let's get going.

 >      bash# git clone https://github.com/tangowhisky37/RaspiPythonProjects.git

* Change into the folder containing the code for the browser controller GoPiGo robot.

 >      bash# cd Gopigo_Robot_Browser_Controlled

### Installing The Dependencies
* Let's get started with the installation. But before we do that we need to make the browser_stream_setup.sh script executable

 >      bash# chmod +x ./browser_stream_setup.sh

* Execute the script to kick off the installation

 >      bash# sudo ./browser_stream_setup.sh

* During the installation you will see errors about mjpg-streamer. Don't stress we will manually install them next.
* Once the installer has done it's job open up a console and download the fork of mjpg-streamer for the Raspberry Pi from github.

 >      bash# git clone https://github.com/jacksonliam/mjpg-streamer

* The above project is a fork of http://sourceforge.net/projects/mjpg-streamer/ with added support for the Raspberry Pi camera via the input_raspicam plugin.
* mjpg-streamer is a command line application that copies JPEG frames from one or more input plugins to multiple output plugins. 
* It can be used to stream JPEG files over an IP-based network from a webcam to various types of viewers such as Chrome, Firefox, Cambozola, VLC, mplayer, and other software capable of receiving MJPG streams.
* It was originally written for embedded devices with very limited resources in terms of RAM and CPU. 
* Its predecessor "uvc_streamer" was created because Linux-UVC compatible cameras directly produce JPEG-data, allowing fast and perfomant M-JPEG streams even from an embedded device running OpenWRT. 
* The input module "input_uvc.so" captures such JPG frames from a connected webcam. mjpg-streamer now supports a variety of different input devices.   
* You must have cmake installed. You will also probably want to have a development version of libjpeg installed. We used libjpeg8-dev based on guidance from the developers. e.g.
* So let's proceed, install the dependencies for mjpg-streamer and then compile, build and install mjpg-streamer from source.

 >      bash# sudo apt-get install cmake libjpeg8-dev

* The following commands will build and install all plugins that can be compiled.

 >      bash# cd mjpg-streamer-experimental
 >      bash# make
 >      bash# sudo make install

### Running The Robot Web Server Application
* With all the installation now out of the way you are now able to proceed with launch of the streaming, browser control program.
*  Make robot_web_server.py executable

 >      bash# chmod +x robot_web_server.py

* Run robot_web_server.py which launches the Python Tornado web server
* Open a web browser on any computer or mobile device and enter the following in the address bar:

 >      http://IP_Address_Of_Your_Raspberry_Pi:98

* The page that hosts the streaming video and browser control application runs on the local IP address of the Pi on port 98
* The video stream would load up and you can use the joystick on the screen to control the GoPiGo

![ GoPiGo ](https://raw.githubusercontent.com/DexterInd/GoPiGo/master/GoPiGo_Chassis-300.jpg)

![ GoPiGo ](https://raw.githubusercontent.com/DexterInd/GoPiGo/master/GoPiGo_Front_Facing_Camera300.jpg)

Enjoy and keep hacking !!!
