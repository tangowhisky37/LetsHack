
## Integrating micro:bit with Scratch (Microsoft Windows Only)

This tutorial covers installation and configuration of all the software required to be able to interact with Scratch (https://scratch.mit.edu) and the micro:bit (https://microbit.org). We will go over all the essential pieces of software, configure them and then test things out by launching scratch on our desktop.

This tutorial only covers integration of Scratch with micro:bit on Microsoft Windows machines. If you are using an Apple machine with macos please see ScratchX (https://scratchx.org).

There are a few ways to interact with Scratch. Let's quickly go over them below - 

* Scratch to micro:bit bridge - You can use the scratch to micro:bit bridge, developed by MrYslab: https://github.com/MrYsLab/s2m
* ScratchX MacOS extension - If you're using Mac OSX, you can install this plugin with the scratch device manager: https://llk.github.io/microbit-extension/
* Connect to Scratch over Bluetooth - You can use the S2Bot App plug-in with Scratch, which allows any compatible BLE controller to interact directly with Scratch project: http://www.picaxe.com/BBC-microbit/

So if you are using an Apple MAC you do not have to bother with rest of this tutorial. Just head over to the link (second link) above and start creating your interactive Scratch programs using Scratch and the micro:bit.

For additional information please head over to - https://github.com/carlosperate/awesome-microbit/blob/master/README.md#scratch-extensions

### What Are Some Of The Features Of Scratch 

Scratch is a visual programming language and online community targeted primarily at children. Using Scratch, users can create their own interactive stories, games and animations, then share and discuss their creations with one another. Developed by the Lifelong Kindergarten group at the MIT Media Lab, the service is designed to help children (ages 8 and up) learn to think creatively, reason systematically and work collaboratively. Scratch is translated into 70+ languages and is used in homes, schools, and after-school clubs in every country in the world. Scratch is often used in teaching coding, computer science, and computational thinking. Teachers also use it as a creative tool across many other subjects including math, science, history, geography, and art. 

As of late 2017, there were more than 22 million registered members of the Scratch online community and more than 26 million shared projects, with roughly 25,000 new members and 30,000 new projects every day. The blocks-based grammar of Scratch has influenced many other programming environments and is now considered a standard for introductory coding experiences for children. Some important statistics about Scratch - 

* Developer: MIT Media Lab Lifelong Kindergarten Group
* Was Influenced By: Snap!
* Implementation language: Squeak (Scratch 0.x, 1.x); ActionScript (Scratch 2.0); HTML5 (Scratch 3.0)
* Suported OS : Windows, macOS, Linux

### What Are Some Of The Features Of micro:bit

The Micro Bit is an ARM-based embedded system designed by the BBC for use in computer education in the UK. The BBC micro:bit is a pocket-sized codeable computer with motion detection, a built-in compass and Bluetooth technology, which was given free to every child in year 7 or equivalent across the UK in 2016. The BBC micro:bit is the result of a collaboration between 29 partners. The BBC micro:bit is the BBC's most ambitious education initiative in 30 years, with an ambition to inspire digital creativity and develop a new generation of tech pioneers.

The board measures 4 cm × 5 cm and has an ARM Cortex-M0 processor, accelerometer and magnetometer sensors, Bluetooth and USB connectivity, a display consisting of 25 LEDs, two programmable buttons, and can be powered by either USB or an external battery pack. The device inputs and outputs are through five ring connectors that form part of a larger 23-pin edge connector.

* CPU: Nordic Semiconductor nRF51822, 16 MHz ARM Cortex-M0 microcontroller, 256 KB Flash, 16 KB RAM.
* Board Connectivity: Bluetooth LE, MicroUSB, edge connector

### Installing and Integrating Scratch and micro:bit

Among the approaches listed at the start of this tutorial the one we are going to follow is the one that uses the Scratch to micro:bit bridge. This project is hosted at github and you can see the details here [MrYsLab](https://github.com/MrYsLab/s2m) and read the documentation here [Documentation](https://mryslab.github.io/s2m/). 

The steps included in the approach are - 

* Step 1 - Install Scratch 2 on your computer
* Step 2 - Install Python for windows on your computer
* Step 3a - Install the micro:bit mu editor or just download the code provided
* Step 3a - Install the s2m script on to the micro:bit using the mu editor
* Step 4 - Install the s2m software on your computer
* Step 5 - Run the s2m program and start developing programs/games that allow the micro:bit to interact with Scratch

#### Step 1 - Installation of Scratch 2 on Windows

Head over to the Scratch website and download Scratch for Windows. You can access the Scratch download for windows here - [Download](https://scratch.mit.edu/download). Please make sure your computer has Adobe AIR installed without which Scratch 2 for Windows will not install. Adobe AIR is a pre-requisite for Scratch 2 on Windows. 

#### Step 2 - Install Python for Windows

Now that we have Scratch installed it's time to head over to the Python website and install Python on our computers. So let's head over to [Python Downloads](https://www.python.org/downloads/windows/) and download the 2.7.xx version of Python for our system. 

Please note that if you are using a 32 bit machine you will need to download a 32 bit version of Python and if you are using a 64 bit machine you will need to download a 64 Bit version of Python from the website. The current release of Python for Windows is 2.7.15 and is accessible at [Downloads](https://www.python.org/downloads/release/python-2715/). 

So go ahead, download the relevant version of Python (32 or 64 bit) to your machine and have it installed. If you are not sure which version to use please head over to windows/control panel/system and look at the system information to understand if you are running a 32 or 64 bit machine. 

**Note - While installing Python please ensure that you choose the "Add Python Executable to Path" option. This will ensure that you are able to access Python from the windows command prompt. If you forget to do this you will either need to manually add the Python binary directory to the system path variable or just un-install + re-install selecting the "Add Python Executable to Path" on the next attempt. If you miss this step you will not be able to run s2m from the windows command prompt.**

#### Step 3a - Download and Install the mu Editor on Your Computer

The next step requires you to head over to the mu editor website, download mu and have it installed on your computer. The mu editor is required to create the hex program file with the python code in it and copy that code over to the micro:bit. You can access the mu editor website here - [https://codewith.mu/](https://codewith.mu/). 

Once you have installed the mu editor you will need to download the python program from the following link - [Python Code Here](https://mryslab.github.io/s2m/install/#installing-the-s2m-microbit-script-on-the-microbit). Copy the code into the mu editor and Flash the script onto the micro:bit by clicking on the Flash button in the editor. 

#### Step 3b - Download and Install the hex File Directly Onto Your Computer

If you want to avoid downloading of the mu editor and creating the hex file you can directly download the hex file we have created using the code provided here - [Download Hex file](https://github.com/tangowhisky37/LetsHack/blob/master/downloads/microbit/s2m.hex). Once you have downloaded the hex file drag the hex file directly onto your micro:bit using windows explorer and it will copy the code onto the micro:bit. 

#### Step 4 - Install the S2M software 

We've now completed installation of Scratch, followed by installation of Python 2.7.xx (32bit or 64 bit version) followed by installation of mu editor to flash the micro:bit with the code provided. You can now proceed with installation of the s2m software on your machine.

So let's open up a windows command console and key in the following commands. You can access the windows command prompt by going into windows/run and then typing "cmd".

> `c:> pip install s2m`

You should now see a whole lot of activity on your machine. This is python downloading the required s2m packages including dependencies from the internet and installing it on your machine. 

#### Step 5 - Running s2m and launching Scratch

With the installation of s2m now complete you will need to open up a command window and then launch s2m. You can access the windows command prompt by going to windows/run and then typing "cmd". Once you have the command prompt open type the following to launch s2m and scratch.

> `c:> s2m`

S2m now launches, detects the communication (com) ports that your micro:bit is connected to and allows Scratch to integrate with micro:bit using the additional blocks provided.

### Design games and interactive programs using Scratch & micro:bit

You should now be able to create programs that allow the micro:bit to interact with Scratch. See the additional blocks provided in scratch 2 which are designed to allow capture of input from the micro:bit. You will need to make sure that you have the micro:bit connected to your machine at all times for this to work. Also, if you are developing other programs using your micro:bit you will need to go back and re-load the hex file provided above before S2M can detect the micro:bit and allow Scratch 2 to interact with the micro:bit.


Thanks!!! Keep hacking!!!

