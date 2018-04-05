# Installation
- [Tutorials](#tutorials)
- [Flashing bin file](#flashing-the-firmware-bin-file)
  - [Esptool](#esptool)
  - [Esptool-gui](#esptool-gui)
  - [NodeMCU-flasher](#nodemcu-flasher)
- [Compiling using Arduino IDE](#compiling-using-arduino-ide)
- [Installation tips and tricks](#installation-tips-and-tricks)
  - [Flash Button / espcomm_open error](#flash-Button-and-espcomm_open-error)
  - [Drivers and COM Port](#drivers-and-com-port)
  - [Upload Settings](#upload-settings)
    - [Flash Mode](#flash-mode)
    - [Flash Frequency](#flash-frequency)
    - [CPU Frequency](#cpu-frequency)
    - [Reset Method](#reset-method)
    - [Baud Rate](#baud-rate)
    - [Flash Size](#flash-size)

## Tutorials

**Online interactive step by step tutorial by [@jLynx](http://github.com/jLynx)**:  
🎓 [http://deauth.me](http://deauth.me)  

**$3 WiFi Jammer/Deauther using ESP8266 | Deauther 2.0 Flashing/Installation  by [@PwnKitteh](https://github.com/PwnKitteh)**:  
🎬 [https://youtu.be/wKhSlIYQ5jA](https://youtu.be/wKhSlIYQ5jA)

## Flashing the firmware bin file

You can find precompiled .bin files on the [release page](https://github.com/spacehuhn/esp8266_deauther/releases). Be sure to download the latest version. The 1 MB file should be good for most devices. If you have a NodeMCU with an ESP-12 you can also use the 4MB file. But all in all, it shouldn't matter that much.  
Use one of the following software to flash your ESP8266 with the .bin file.  

### Esptool
Using the NodeMCU (or any similar development board), the flash location is 0x0000 and the mode is qio.  
`esptool.py -p /dev/ttyUSB0 write_flash -fm qio 0x0000 esp8266_deauther.ino.nodemcu.bin`  
Where `/dev/ttyUSB0` is the COM port of your device, `write_flash` is telling the program to write to flash memory, `-fm qio` is mode qio, which is the mode for chips with 4MB or more, and `esp8266_deather.ino.nodemcu.bin` is the name of your .bin file. 

### Esptool-gui
An easy to use GUI flasher for Windows and Mac: [esptool-gui](https://github.com/Rodmg/esptool-gui).  
Select the COM Port and the .bin file (firmware), then just press upload.  

### NodeMCU-flasher
Another easy to use GUI flasher, but this time only for Windows: [nodemcu-flasher](https://github.com/nodemcu/nodemcu-flasher).  
Select the COM port, go to config and select your .bin file at *0x000000*.   
Go back to Operation and click Flash.  
![Recommended Flash settings NodeMCU Flasher](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/flash_settings_nodemcu_flasher.jpg)  

⚠️ The NodeMCU Flasher is outdated and can be buggy. If it doesn't work, just try flashing it again and see the [Installation tips and tricks](#installation-tips-and-tricks).  

## Compiling using Arduino IDE
0) First you have to install and open the [Arduino IDE](https://www.arduino.cc/en/main/software).  

1) In Arduino go to File -> Preferences add *both* URLs in *Additional Boards Manager URLs*  
- `http://arduino.esp8266.com/stable/package_esp8266com_index.json`
- `http://phpsecu.re/esp8266/package_deauther_index.json` 

![External PICTURE adding board url](https://raw.githubusercontent.com/tobozo/Arduino/deauther/screenshots/board_manager_urls.jpg)

2) Go to Tools -> Board -> Boards Manager, search "esp8266" and install `esp8266` first, then `arduino-esp8266-deauther`  
![External PICTURE installing sdk](https://raw.githubusercontent.com/tobozo/Arduino/deauther/screenshots/board_manager_sdk.jpg)

3) Select your board at Tools -> Board and be sure it is at `ESP8266 Deauther Modules` (and **not** at `ESP8266 Modules`)!  
![External PICTURE select board](https://raw.githubusercontent.com/tobozo/Arduino/deauther/screenshots/screenshot_select_board.jpg)

4) Download the source code for this project from the [releases page](https://github.com/spacehuhn/esp8266_deauther/releases). You can also clone the project to get the latest changes, but you will also get the latest bugs ;)

5) Extract the whole .zip file, navigate to esp8266_deauther and open esp8266_deauther.ino with Arduino.

6) Check your upload settings and press upload!

7) You might want to adjust the display, LED and button configurations. You can do that in the `A_config.h` file (second tab in Arduino). You can also find predefined config files for certain boards in the [configs folder](https://github.com/spacehuhn/esp8266_deauther/tree/master/configs).  

## Installation tips and tricks
These are some small tips that are beneficial for first time users of this software, and hopefully will make it more accessible and cause less headache when flashing the board.  
We recommend the [esptool](https://github.com/espressif/esptool) for flashing .bin files, because it works on all platforms. You can read more about how esptool works on their github page, linked above.  
For customized versions, we highly recommend using Arduino and our Deauther SDK (see Compiling using Arduino IDE).

### Flash Button and espcomm_open error
💥❗️❓❗️❗️💢 Sometimes everything is right but it won't upload and you maybe get an error like `error: espcomm_open failed`.  
What you have to do is hold the flash button down, start uploading and **only release it when you see that it's started uploading**.  
![PICTURE nodemcu flash button](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/nodemcu_flash_buttons.jpg)

Most development boards feature a auto-reset method and sometimes it doesn't work properly and it fails to go into flashing mode automatically. To manully force it into the flashing mode, you have to hold down the button.   

### Drivers and COM Port
To upload you always have to select the correct COM port. You can think of it as the address with that your computer accesses the ESP8266.  
The best way to find the correct port is to open the Arduino IDE and see what ports are listed there. This looks the same for every OS, including Linux. On Windows, COM1 is usually never the correct port.  
On Windows you can also have a look at your device manager, there you can also see if a device is not recognized.

If non of the COM ports work correctly or you can't find any COM Port, you might need to install the drivers.  
The driver you need depends on the UART (USB to Serial) chip that is used on your development board.  
Those are the drivers of the most used chips:  
- 💾 [CP2102](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
- 💾 [CH340](https://sparks.gogo.co.nz/ch340.html)

![PICTURE serial chips](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/nodemcu_serial_modules.jpg)  

If you're not sure which chip your board is using, just try both.  

When this also doesn't help, try out different cables (some USB cables are only for charging and don't have data lines).  

### Upload Settings
Those are the recommended upload/compile settings for Arduino:
```
Board: Generic ESP8266 Module  
Flash Mode: DIO
Flash Frequency: 80 MHZ
CPU Frequency: 160 MHz
Flash Size: 1M (256K SPIFFS)
Reset Method: nodemcu
Upload Speed: 115200
Port: <com port of your device>
```
Most NodeMCUs and other development boards have 4MB Flash so you can set the Flash Size to 4M (3M SPIFFS) or select NodeMCU 1.0 as the board.  
Changing the Flash size can give you more SPIFFS for saving data, scripts or other files.  
If you have a board with the ESP-07 (the one with the connector for an external antenna) it probably only has 1MB of flash, so keep the recommended settings above.  
Putting the Upload Speed to 921600 or changing the Flash Frequency to 80MHz gives you higher upload speeds but doesn't always work.  

#### Flash Mode
DIO should always work. It means Dual In-/Output.  
QIO (quad I/O) uses 4 instead of 2 pins and it should make the flash faster, but you won't be able to use GPIO 9 and 10 (SD2, SD3)! If you flash it with QIO and use those pins, it will crash without a warning.  
More details on the different modes are descripted here: https://github.com/espressif/esptool/wiki/SPI-Flash-Modes

#### Flash Frequency
Like with the flash mode, just try out what works the best.  

#### CPU Frequency
We strongly recomment to use 160MHz to get the extra performance out of the chip.  

#### Reset Method
Again, try out what works and use that.  

#### Baud Rate
The recommended baud rate for uploading is 115200. You can try higher baud rates for faster uploading or slower ones if 115200 isn't working very reliable.  

#### Flash Size
The flash size is an important factor!  
![PICTURE different esp8266 modules](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266/img/esp_modules.jpg)  
The ESP-12 (which is used on most development boards like the NodeMCU) has 4MB of flash memory.  
Other Modules like the ESP-01 and ESP-07 (the one with the antenna connector) come with only 1MB of memory.  
You have to change your upload settings depending on the module you're using.  

For compiling we recomment to use either `1M (256K SPIFFS)` or `4M (3M SPIFFS)`.  