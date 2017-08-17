
###  Alexa and the Raspberry Pi

Amazon's Alexa-controlled Echo speaker is a wireless speaker. But it's capable of much more. Using nothing but the sound of your voice, you can search the Web, create to-do and shopping lists, shop online, get instant weather reports, and control popular smart-home products—all while your phone stays in your pocket. Thanks to Amazon opening up the Alexa Developer API's we now are able to access Alexa on the Raspberry Pi. This project was initially started by Sam Machin based in the UK but soon grabbed international attention when makers, hackers from all around the world realized that they could turn their Raspberry Pi's into Alexa devices as well. 

~[Alexa](https://raw.githubusercontent.com/tangowhisky37/RasPiSetupGuide/master/images/alexa.jpg)

This document provides a tutorial on the installation of [AlexaPi](https://github.com/alexa-pi/AlexaPi) on the Raspberry Pi. This document was originally authored by the AlexaPi team and can also be read at [AlexaPi](https://github.com/alexa-pi/AlexaPi/wiki/Installation)

### Register at Amazon

First you need to obtain a set of credentials from Amazon to use the Alexa Voice service. Make a note of these credentials as you will be asked for them during the install process.

- Login at [https://developer.amazon.com](https://developer.amazon.com) and go to `ALEXA`, then `Alexa Voice Service`.
- `Register a Product Type` > `Device`. 
- You are at `Device Type Info` left tab.
    - For the `Device Type ID` and `Display Name` use something like _AlexaPi_ or whatever you want.
     - `Next`
- You are at `Security Profile` left tab.
    - From the drop-down menu choose `Create a new profile`. 
    - Choose whatever for `Security Profile Name` and `Security Profile Description`. Hit `Next`.
    - Under `Web Settings` horizontal tab hit `Edit` and: 
        - `Allowed Origins` - put there `http://localhost:5050` and `http://ALEXA.DEVICE.IP.ADDRESS:5050` 
        - `Allowed Return URLs` put `http://localhost:5050/code` and `http://ALEXA.DEVICE.IP.ADDRESS:5050/code`. 
        You have to replace `ALEXA.DEVICE.IP.ADDRESS` with the IP (for example 192.168.1.123) of your AlexaPi device (for example Raspberry Pi). This is especially necessary when you are installing from another computer than AlexaPi is gonna run on.
- Fill some of the other stuff in.

### Install AlexaPi

1. Boot your PC and login to a command prompt.
2. Make sure you are in `/opt` by issuing

    ```
    bash# cd /opt
    ```
3. Make sure you have git installed
    
    ```
    bash# sudo apt-get install git # For Debian OSs (Debian, Raspbian, OSMC, OpenElec...)
    bash# sudo pacman -Sy git # For Arch Linux
    ```

4. Clone this repo
    
    ```
    bash# sudo git clone https://github.com/alexa-pi/AlexaPi.git
    ```
    
    NOTE: You can also clone the repository to any other directory (and lose the `sudo` here, if you have permission to write to that directory), but you won't be able to run AlexaPi on boot with our init scripts. It is therefore recommended for advanced users (who know what they're doing) only.     

5. Run the setup script

    ```
    bash# sudo ./AlexaPi/src/scripts/setup.sh
    ```

    Follow instructions...

### Post-installation steps

Now that you have installed AlexaPi there's a couple of things you need to do.

- Reboot your machine **or** start AlexaPi with 
    ```
    sudo systemctl start AlexaPi.service
    ```
- Check the status of AlexaPi with 
    ```
    sudo systemctl status AlexaPi.service
    ```
    If it is not running, be sure to see the full **[logs](https://github.com/alexa-pi/AlexaPi/wiki/Debugging#logs)**.

- In a lot of cases, you have to **setup your input / output devices properly** in the configuration file. Read the **[Audio setup & debugging](https://github.com/alexa-pi/AlexaPi/wiki/Audio-setup-&-debugging)** section in the documentation.

- If you have a **desktop OS** (such as default Raspbian), you have to set up **[system-wide PulseAudio](https://github.com/alexa-pi/AlexaPi/wiki/Audio-setup-&-debugging#pulseaudio)**. You usually get _dbus_ and _pulseaudio_ error in the log if you don't do this.

- If you got this working, but **audio playback is choppy**, try changing the playback handler in the [config](https://github.com/alexa-pi/AlexaPi/wiki/Configuration-file) from _vlc_ to _sox_. This will be default in later versions of AlexaPi. If you're using pulseaudio, please read [audio setup guide](https://github.com/alexa-pi/AlexaPi/wiki/Audio-setup-&-debugging#running-pa-in-system-wide-mode-recommended).

It might also be a good idea to read the detailed [DOCUMENTATION](https://github.com/alexa-pi/AlexaPi/wiki) before heading off to the forums and asking questions.

Enjoy :)

