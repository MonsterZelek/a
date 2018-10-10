# ❓ FAQ

![Please don't](https://pbs.twimg.com/media/Dgn7wrnV4AEJZqr.jpg)

## Overview
- [How to Reset / I forgot the password](#how-to-do-a-reset)
- [5GHz Support](#5ghz-support)
- [ESP32 and ESP8285 Support](#esp32-and-esp8285-support)
- [Difference between Jammer and Deauther](#difference-between-jammer-and-deauther)
- [Why is there no Packet-Monitor/Deauth-Detector in the web interface?](#why-is-there-no-packet-monitordeauth-detector-in-the-web-interface)
- [How to compile .bin files yourself](#how-to-compile-bin-files-yourself)
- [Drivers](#drivers)
- [Fix crashed](#fix-crashes)
- [Not able to connect to Access Point](#not-able-to-connect-to-access-point)
- [Removing Deauther](#removing-deauther)
- [espcom error](#espcom-error)
- [Language doesn't change](#language-doesnt-change)
- [Error writing/saving/reading file](#error-writingsavingreading-file)

## How to do a Reset
If you just want to reset the settings you can open a serial connection and type in `reset`.  
The easiest way to do that is using the Arduino Serial monitor. The baudrate is `115200` with `Newline`.  
To erase the Deauther script including the WiFi credentials and everything that is saved in the SPIFFS, use our reset sketch:
https://github.com/spacehuhn/esp8266_deauther/tree/master/Reset_Sketch  
You can either compile and flash the .ino file with Arduino or flash one of the .bin files.  

## 5GHz Support
The ESP8266 supports 2.4GHz WiFi, which is already very impressive if you think about how small, powerful, accessible and affordable this system on a chip is!  
A lot of people are asking for 5GHz support, however **this project is not able to do that**.  
As of right now (2018) no hackable 5GHz SoC is available in the form of something like the ESP8266.  
Even if someone would make such a chip, it would be incompatible with this software.  
You could build a dual band Deauther with a Raspberry Pi and the right WiFi module.  
But as of right now, it's not always easy to find good Dual-Band WiFi chips that support packet injection and monitor mode.

**⚠️ THE ESP8266 DOES NOT AND WILL NOT SUPPORT 5GHZ! ⚠️**

Devices supporting this are more expensive and need special drivers (this will change in the future as new chips are released all the time).
But if you want to try it, look for the `rtl8812au` or `rtl8811au` WiFi modules. Those have already been used to inject packets at 5GHz.  

## ESP32 And ESP8285 Support
ESP32: No  
ESP8285: Yes  
See [Supported Devices](https://github.com/spacehuhn/esp8266_deauther/wiki/Supported-Devices) for more details.  

## Difference between Jammer and Deauther
While a jammer just creates noise on a specific frequency range (i.e. 2.4GHz), a deauthentication attack is only possible due to a vulnerability in the WiFi (802.11) standard. The deauther does not interfer with any frequencies, it is just sending a few WiFi packets that let certain devices disconnect. That enables you to specifically select every target. A jammer just blocks everything within a radius and is therefore highly illegal to use.

Watch this video for a good explanation on the technical and legal differences: 🎬 [WiFi Jammers vs Deauthers | What's The Difference?](https://www.youtube.com/watch?v=6m2vY2HXU60)  

## Why is there no Packet-Monitor/Deauth-Detector in the web interface?
The problem is that you can't have an access point open to host the web server while sniffing WiFi.  
It's like with every other WiFi card. Either you use it as an access point to host a network, as a station to connect to one or you put it in monitor mode to sniff for packets. But you can't have everything at the same time.  

## How to compile .bin files yourself
In Arduino click `Sketch` -> `Export compiled Binary` and a new .bin file will be created in the sketch folder.

## Drivers
If you can't find the COM port of your device, then you probably haven't installed the right drivers yet.
Here are the links to the drivers of the 2 most used UART chips:
- 💾 [CP2102](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
- 💾 [CH340](https://sparks.gogo.co.nz/ch340.html)

If you're not sure which chip your board is using, just try both.

## Fix crashes
A crash or exception can have a lot of reasons but before you open a new issue, try this:  
- open a serial connection
- type `reset` to reset all settings
- type `format` to remove all saved files in the on-board file system
- reconnect your device and see if it works now

## Not able to connect to Access Point
There could be a lot of reasons why you can't connect to the ESP8266 with certain devices.  
For example, someone reported that the Intel 7260 WiFi Chip can make problems: https://github.com/spacehuhn/esp8266_deauther/issues/754  
Arduino has example sketches for the ESP8266 to create an access point. You can try that out and see if you can connect to it. If not, then the problem is not related to this project's code and you have to investigate your hardware/software setup further.  

## Removing Deauther
To erase the deauther you can just flash a different sketch. To overwrite the SPIFFS and EEPROM, you can flash our simple [Reset Sketch](https://github.com/spacehuhn/esp8266_deauther/tree/master/Reset_Sketch).  

## espcom error
The `espcom opening` or `espcomm_sync failed` error tells you that your computer couldn't connect to the ESP8266 correctly when trying to upload something.  
Be sure you have the correct COM port selected and use the correct [upload settings](#upload-settings).  
If you can't find the COM port, read [Finding COM Port](#finding-com-port) first.  
Maybe you need to [install the drivers](#drivers).  
Also be sure you use a USB data cable! Sometimes it also helps to restart Arduino or your computer, changing the cable or USB port.  
It was also reported that the Windows-Insider-Program can make problems with the cp2102 drivers.  

If everything else fails, try reflashing the Deauther. See [Removing Deauther](#removing-deauther) and then flash it again.  

## Language doesn't change
If you go to Settings in the web interface, you can change the language. For example `de` is for the German language file.  
To see what languages are supported, have a look at the [lang folder](https://github.com/spacehuhn/esp8266_deauther/tree/master/web_interface/lang) or the description of the latest [release](https://github.com/spacehuhn/esp8266_deauther/releases).  
If the language doesn't change, it is probably because your browser has the old language file cached and doesn't want to reload it. Try deleting your browser cache.  
Or open `192.168.4.1/lang/default.lang` and reload it one or two times.  

## Error writing/saving/reading file
If you get message like `Error saving file` or something similar over serial, there is probably something wrong with the SPIFFS. It happens sometimes that the file system get corrupted for some reason. Usually you can fix it by running the `format` command and then restarting the device.  
If the error persists, please be sure that your [upload settings](https://github.com/spacehuhn/esp8266_deauther/wiki/Installation#upload-settings) are correct, especially the [flash size](https://github.com/spacehuhn/esp8266_deauther/wiki/Installation#flash-size).  