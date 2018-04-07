**Overview:**
- [Drivers](#drivers)
- [It's not working](#its-not-working)
- [Fix crashed](#fix-crashes)
- [Removing Deauther](#removing-deauther)
- [Espcom opening error](#espcom-opening-error)
- [Language doesn't change](#language-doesnt-change)

## Drivers
If you can't find the COM port of your device, then you probably haven't installed the drivers or they are not working correctly.
Here are the links to the drivers of the 2 most used UART chips:
- 💾 [CP2102](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
- 💾 [CH340](https://sparks.gogo.co.nz/ch340.html)

If you're not sure which chip your board is using, just try both.

## It's not working
Here are a few things you can try if it isn't working.
- Does the USB cable have data lines? This seems weird, but not every cable does, and it might be a reason of why the board isn't showing up in the program
- Maybe the chip randomly broke, try flashing another program onto it.

## Fix crashes
A crash or exception can have a lot of reasons but before you open a new issue, try this:  
- open a serial connection
- type `reset` to reset all settings
- type `format` to remove all saved files in the SPIFFS
- dis- and reconnect your device and see if it works now

## Removing Deauther
To erase the deauther (inclusing SPIFFS and EEPROM), please flash our simple [Reset Sketch](https://github.com/spacehuhn/esp8266_deauther/tree/master/Reset_Sketch).  

## espcom opening error
The `espcom opening error` tells you that your computer couldn't connect to the ESP8266 correctly when uploading.  
Be sure you have the correct COM port selected and the correct [upload settings](#upload-settings).  
If you can't find the COM port, read [Finding COM Port](#finding-com-port) first.  
Maybe you need to [install the drivers](#drivers).  
Also be sure you use a USB data cable! Sometimes it also helps to restart Arduino or your computer, changing the cable or USB port.  

If everything else fails, try reflashing the deauther. See [Removing Deauther](#removing-deauther) and then flash it again (we recommend esptool.py).  

## Language doesn't change
If you go to Settings in the web interface, you can change the language. For example `de` is for the German language file.  
To see what languages are supported, have a look at the [lang folder](https://github.com/spacehuhn/esp8266_deauther/tree/master/web_interface/lang) or the description of the latest [release](https://github.com/spacehuhn/esp8266_deauther/releases).  
If the language doesn't change, it is probably because your browser has the old language file cached and doesn't want to reload it. Try deleting your browser cache.  
Or open `192.168.4.1/lang/default.lang` and reload it one or two times.  

