
### What Is The RaspiSetupGuide About

The HowTo guides that I have put together have mostly been written up as notes to myself. These notes to myself were intended to serve as a reminder for the various systems administration tasks I usually perform when i pick up a new Raspberry Pi and need to setup the device integrating it with my existing lab setup at home. Over a period of time site this has evolved to also include most of the common systems administration tasks one would need to perform when running Linux (Raspbian) operating system on the Raspberry Pi. A point also worth noting is that The collection of articles initially focused on the Raspberry Pi but over a period of time as I began hacking with the Arduino Uno, Ardino MEGA, ESP8266, ESP32, etc. I've ended up listing all of those relevant projects and HowTo's as well.

Hopefully some of the information here will be useful to some of you out there who might stumble across simliar issues when hacking with your own Raspberry Pi, Arduino, ESP8266 or ESP32. 

### HowTos -
* [Custom Node Red Installation](/Node-Red-Setup.md) 
* [Git Tutorial](/Git-Tutorial.md)
* [Hacking the Disk Layout on a Raspberry Pi Model A](/Custom-Disk-Prep.md)
* [Installing Alexa on the Raspberry Pi](/Alexa-On-Raspberry-Pi.md)
* [Setting up your Raspberry Pi to monitor your home remotely using Rpi Cam](/Webcam-Setup.md)
* [Turn your Raspberry Pi 3 into a smart audio streaming solution using Mopidy](/Mopidy-Audio-Setup.md)
* [Youtube on the Command Line](/Youtube-On-CommandLine.md)

### Just Code : Projects Completed + Projects Under Development -
* [Blink LED's - Interacting with LED's through GPIO](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/BlinkLEDs)
* [Detection motion using a PIR Sensor and raising an alarm](https://github.com/tangowhisky37/RaspiPythonProjects/blob/master/PIR) 
* [Interacting with Analog Sensors (PIR Module) using the ADC (MCP 3008) and the Raspberry Pi](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/ReadingAnalogSensors)
* [IoT - Obtain Temperature & Humidity using the DHT11 & uploading data to ThingSpeak](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Sense_Temp_Humidity)
* [IoT - Obtain Temperature & Humidity data from the Arduino MEGA (DHT 11) & uploading data to ThingSpeak](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Sense_Temp_Humidity_Pull_Data_Arduino)
* [IoT - Weather data acquisition using OWM and upload to ThingSpeak](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Weather_Reporting)
* [IoT - Weather data acquisition and write to LCD](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Write_To_LCD_Screen)
* [IoT - Weather data acquisition and write to Twitter](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Write_Weather_To_Twitter)
* [Robotics - GoPiGo obstacle avoidance robot](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Gopigo_obstacle_avoidance_robot)
* [Robotics - GoPiGo keyboard controlled robot](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Gopigo_robot_keyboard_conrolled)
* [Robotics - GoPiGo browser controlled robot](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/Gopigo_Robot_Browser_Controlled)
* [Face detection usuing : Python + OpenCV + Raspberry Pi Camera + Amazon Web Services (AWS)](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/OpenCV)
* [Simple Face detection : Python + OpenCV + AWS Rekognition](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/OpenCV/CaptureFaces)
* [Detecting faces in a video stream : Python + OpenCV + AWS Rekognition](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/OpenCV/CaptureSingleImage)
* [Detecting faces in a video stream + STT (Speech To Text) : Python + OpenCV + AWS S3 + AWS Rekognition](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/OpenCV/CaptureVideoStream)
* [Face detection using Python + OpenCV + AWS S3 + AWS Rekognition with multiple faces within the source image](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/OpenCV/CaptureVideoStream_MultipleSourceFaceNoLambda)
* [Sensing light using the Photo Resistor Light Sensor Module](https://github.com/tangowhisky37/RaspiPythonProjects/tree/master/LightSensor)

### In The Works - 
* Evolution of the Raspberry Pi
* Overview of the Raspberry Pi 3
* Burning the SD Card & Booting up your Raspberry Pi
* Configuring your Raspberry Pi to connect to a Wireless Network
* Performing basic configuration on your Raspberry Pi using "raspi-config"
* Setting up your Raspberry Pi for remote (Command Line) access using SSH
* Setting up your Raspberry Pi for remote (GUI) access using VNC
* Setting up your RaspberryPi 3 to able to VNC (remote connection) to the main display
* Linux survival basics - Introduction to the BASH shell and key commands
* Mounting an external Windows recoginzed USB Device (& File System) on the RaspberryPi 3
* ~~Setting up your Raspberry Pi to monitor your home remotely using Rpi Cam~~
* Setting up a USB Web Camera on Raspberry Pi 3 
* Configuring the Raspberry Pi to play audio, video
* Interacting with the real world using GPIO. Build simple circuits. 
* Changing the default sound output on the Raspberry Pi 3
* Installing and testing a USB mike on the Raspberry Pi 3
* ~~Installing Alexa on the Raspberry Pi~~
* ~~OpenCV - Face detection using AWS S3, AWS Rekognition, AWS Lambda. Read out current weather on positive match.~~
* ~~Turn your Raspberry Pi into a smart audio streaming solution using Mopidy~~
* ~~Hacking the disk layout on a Raspberry Pi Model A~~
* ~~Custom Node Red Installation~~
* ~~Git Introductory Tutorial~~
* ~~Youtube on the Command Line~~

### Important Links - 
* [Raspberry Pi Foundation](http://www.raspberrypi.org)
* [Raspberry Pi Magazine](http://www.raspberrypi.org/magpi/)
* [Arduino.cc](http://www.arduino.cc)
* [Arduino.org](http://www.arduino.org)
* [Cicrcuito - Drag and drop interface to design circuits and auto-generate code](http://wwww.circuito.io)
* [Makezine - Magazine for makers](http://makezine.com)
* [Makezine's guide to boards for makers](http://makezine.com/comparison/boards/)
* [PiBakery - Create pre-configured SD card images for your Raspberry Pi](http://www.pibakey.org)
* [Etcher - Write Raspberry Pi Image to the SD Card](http://etcher.io)
* [Win32DiskImager - Write Raspberry Pi Images to the SD Card](http://sourceforge.net/projects/win32diskimager/)
* [Fritzing - Software to design circuits](http://fritzing.org)

### Thanks for visiting - 
Hopefully you have found some value in the guides that have been published at this site. If you have any input or feedback please drop me an email at trevor at practical performance analyst dot com. You can see the rest of my open contributions at [Github](https://github.com/tangowhisky37)

### Who the hell is tangowhisky37 - 
`tangowhisky37` is the pseudonym that Trevor (Warren) has used for a while now. Its inspired by his love for the physics of aviation. Trevor (Warren) is passionate about challenging the status-quo and finding reasons to innovate. Over the past 15 years he has been delivering complex systems, has worked with very large clients across the world and constantly is looking for opportunities to bring about change. 

His love for working with people and harnessing the power of the collective human intellect he believes helps him deliver the expected outcomes. Trevor constantly strives to combine his passion for delivering outcomes with his ability to build long lasting professional relationships. You can learn more about the work he does at [LinkedIn](https://au.linkedin.com/in/trevorwarren). Visit the [Github](https://github.com/tangowhisky37) for details of the projects he's been hacking with.

