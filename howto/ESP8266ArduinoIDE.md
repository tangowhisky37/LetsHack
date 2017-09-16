
## Arduino core for ESP8266 WiFi chip
The Arduino Core project for ESP8266 creates support for ESP8266 chip within the Arduino environment. It lets you write sketches using familiar Arduino functions and libraries, and run them directly on ESP8266, no external microcontroller required. ESP8266 Arduino core comes with libraries to communicate over WiFi using TCP and UDP, set up HTTP, mDNS, SSDP, and DNS servers, do OTA updates, use a file system in flash memory, work with SD cards, servos, SPI and I2C peripherals.

Starting with 1.6.4, Arduino allows installation of third-party platform packages using Boards Manager. The ESP8266 Arduino Core project has packages available for Windows, Mac OS, and Linux (32 and 64 bit).

### Installing ESP8266 Board Within Arduino 
Install the current upstream Arduino IDE at the 1.8 level or later. The current version is at the Arduino website.

- Start Arduino and open Preferences window. 
- Enter `http://arduino.esp8266.com/stable/package_esp8266com_index.json` into Additional Board Manager URLs field. 
- You can add multiple URLs, separating them with commas.
- Once complete open Boards Manager from Tools > Board menu and install esp8266 platform.
- Don't forget to select your ESP8266 board from Tools > Board menu after installation). 

You can read documentation at - http://esp8266.github.io/Arduino/versions/2.3.0/`

## Additional Links 
- Read documentation for latest development version: https://arduino-esp8266.readthedocs.io/en/latest/
- ESP8266 Arduino Core Project - https://github.com/esp8266/Arduino
- Issues and support - ESP8266 Community Forum is a well established community for questions and answers about Arduino for ESP8266.
- Installation Article at Sparkfun - https://learn.sparkfun.com/tutorials/esp8266-thing-hookup-guide/installing-the-esp8266-arduino-addon
