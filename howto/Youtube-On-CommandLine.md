
## Youtube On The Command Line (CLI)

This tutorial will cover installation and configuration of mps-youtube for purposes of playing youtube videos at the command line. No why would anyone want to play youtube videos at the command line...:). Am sure I could give you quite a few reasons but the most relevant one is, because I can. Ok, so I'll stop behaving like a smarty pants and will tell you why. 

The Raspberry Pi is a small credit card sized computer. Over the years the Raspberry Pi has definitely got a lot faster and a lot more powerful. The current generation of Raspberry Pi 3 sports 4 Arm processor cores and 1 GB of RAM on the tiny little SBC (Single Board Computer). I use my Raspberry Pi to do many things, its almost like my little Linux Server at home running multiple services each performing a different task. One of the tasks I use my Raspberry Pi for is to develop code and to do that generally have a VNC connection open into the Raspberry Pi with multiple teriminal windows open. While hacking code I might also want to listen to generally stream some music from Youtube but to be able to do that I have to run a browser which consumes a large amount of CPU compute power which I reckon could be put to better use in other areas. 

With mps-youtube you can stream audio content from youtube through a terminal window eliminating the need for a browser session to be running. The setup is not that complicated and if you follow the steps in this document you should get up and running or listening to music in this case within 20 mins. So let's get started and dive into the setup of mps-youtube.

### What Are Some Of The Features Of mps-youtube 

mps-youtube is based on mps, a terminal based program to search, stream and download music. The mps-youtube implementation uses YouTube as a source of content and can play and download video as well as audio. The pafy library handles interfacing with YouTube. Here's a summary of the features provided by mps-youtube.

![mps](https://raw.githubusercontent.com/tangowhisky37/RasPiSetupGuide/master/images/mps.png)

* Search and play audio/video from YouTube
* Search tracks of albums by album title
* Search and import YouTube playlists
* Create and save local playlists
* Download audio/video
* Convert to mp3 & other formats (requires ffmpeg or avconv)
* View video comments
* Works with Python 3.x
* Works with Windows, Linux and Mac OS X
* Requires mplayer or mpv

A key point to note is that mps-youtube is based on Python3 and requires the Python3 interpreter installed for it to run. 

### Installing Key Dependencies

Some of the key dependencies for mps-youtube are - 

* [pafy](https://github.com/mps-youtoube/pafy)
* [youtube-dl](https://gitub.com/rg3/youtube-dl/)

Before we can go ahead and install mps-youtube we need to install the above dependencies first. So let's get started.

Head over to [pafy](https://github.com/mps-youtoube/pafy) and download the latest codebase to your Raspberry Pi or instead use git at the terminal to clone the repository.

> `bash# git clone https://github.com/mps-youtoube/pafy`

The above command will clone the pafy codebase to your local disk on the Raspberry Pi. Change into the pafy directory to kick off the build process.

> `bash# sudo python3 setup.py install`

The above command will build the pafy code and then copy the libraries into the relevant Python3 library path on the Raspberry Pi. Make sure that the build and installation have completed without any issue before you move onto installing the next dependency. Now that pafy is out of the way let proceeed with the build and installation of youtube-dl.

Head over to [youtube-dl](https://github.com/rg3/youtube-dl) and download the latest codebase to your Raspberry Pi or instead use git at the terminal to clone th
e repository.

> `bash# git clone https://github.com/rg3/youtube-dl`

The above command will clone the youtube-dl codebase to your local disk on the Raspberry Pi. Change into the youtube-dl directory to kick off the build process.

> `bash# sudo python3 setup.py install`

The above command will build the youtube-dl code and then copy the libraries into the relevant Python3 library path on the Raspberry Pi. Now we could have installed youtube-dl using the existing repository for the Raspberry Pi or using pip but i choose not to do either. I've gone down both the paths and I've had issues getting mps-youtube working hence my recommendation to download the source and get them compiled locally using Python3. That way you know you've got the latest versions of all the libraries. 

There's two final dependencies you'll need to install. Make sure you are installing the Python3 versions of the package.

> `bash# sudo pip3 install dbus-python pygobject`

We are now ready to move onto the next step and consider installation of the mps-youtube package.

### Installing mps-youtube

With installation of both Pafy and youtube-dl out of the way we can now focus on mps-youtube. The steps here are very similar to the above two. 

Head over to [mps-youtube](https://github.com/mps-youtoube/mps-youtube) and download the latest codebase to your Raspberry Pi or instead use git at the terminal to clone th
e repository.

> `bash# git clone https://github.com/mps-youtoube/mps-youtube`

The above command will clone the mps-youtube codebase to your local disk on the Raspberry Pi. Change into the mps-youtube directory to kick off the build process.

> `bash# sudo python3 setup.py install`

The above command will build the mps-youtube code and then copy the libraries into the relevant Python3 library path on the Raspberry Pi. Make sure that the build and installation have completed without any issue. If for whatever reasons the build fails you have to go back and work through the issues involved. If things were to go pear shaped I would recommend grabbing a cup of coffee and making google, patience your best fried.

### Considering Which Music Player To Use

mps-youtube seems to support both mplayer and mpv. I initially tried getting mps-youtube to work with mplayer and for some reason it just wouldn't work. Rather than spending too much effort trying to figure out what I switched to using mpv and it seemed to work out of the box. The only thing being that i have to launch mps-youtube as sudo for it to work. When i have time next i might dive in and work out what's happening there but for now this will do.

So let's go ahead and install mpv and mplayer to be on the safer side.

> `bash# sudo apt-get install mplayer mpv`

With the above complete you are ready to launch mps-youtube. 

### Launching mps-youtube

With the installation of all the dependencies, mps-youtube, mplayer and mpv out of the way you are now ready to launch mps-youtube to play some of your favorite music. Issue the following command to launch mps-youtube.

> `bash# sudo mpsyt`

As mentioned earlier, if you are having issues getting the mps-youtube to play music using youtube, you might need to change the settings and get mps-youtube to play music using mpv. Either ways I would recommend reading through the documentation at the [mps-youtube](https://github.com/mps-youtoube/mps-youtube) github page to see mps-youtube in action and understand the syntax.

Using mps-youtube is super easy and relative light weight on the Raspberry Pi in terms of compute resources as compared to keeping a browser session running just to stream music from youtube.

We hope you've been able to get mps-youtube working and have learned something relevant along the way. 

Thanks!!! Enjoy the music!!!

