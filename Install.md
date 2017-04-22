## Installation

The only thing you will need is a computer and an ESP8266.  

I recommend you to buy a USB breakout/developer board, because they have 4Mb flash and are very simple to use.
It doesn’t matter which board you use, as long as it has an ESP8266 on it.  

You have 2 choices here. Uploading the bin files is easier but not as good for debugging, so keep that in mind in case you want to open an new issue. 
**YOU ONLY NEED TO DO ONE OF THE INSTALLATION METHODS!**

### **Option 1** Uploading the bin files  

**Note:** the 512kb version won't have the full MAC vendor list.  
The NodeMCU and every other board which uses the ESP-12 has 4mb flash on it.

**0** Download the current release from [here](https://github.com/spacehuhn/esp8266_deauther/releases)  

**1** Upload using the ESP8266 flash tool of your choice. I recommend using the [nodemcu-flasher](https://github.com/nodemcu/nodemcu-flasher). If this doesn't work you can also use the official [esptool](https://github.com/espressif/esptool) from espressif.

**That's all! :)**

Make sure you select the right com-port, the right upload size of your ESP8266 and the right bin file.  

If flashing the bin files with a flash tool is not working, try flashing the esp8266 with the Arduino IDE as shown below.

### **Option 2** Compiling the source with Arduino

**0** Download the source code of this project.

**1** Install [Arduino](https://www.arduino.cc/en/Main/Software) and open it.

**2** Go to `File` > `Preferences`

**3** Add `http://arduino.esp8266.com/stable/package_esp8266com_index.json` to the Additional Boards Manager URLs. (source: https://github.com/esp8266/Arduino)

**4** Go to `Tools` > `Board` > `Boards Manager`

**5** Type in `esp8266`

**6** Select version `2.0.0` and click on `Install` (**must be version 2.0.0!**)

![screenshot of arduino, selecting the right version](https://raw.githubusercontent.com/spacehuhn/esp8266_deauther/master/screenshots/arduino_screenshot_1.JPG)

**7** Go to `File` > `Preferences`

**8** Open the folder path under `More preferences can be edited directly in the file`

![screenshot of arduino, opening folder path](https://raw.githubusercontent.com/spacehuhn/esp8266_deauther/master/screenshots/arduino_screenshot_2.JPG)

**9** Go to `packages` > `esp8266` > `hardware` > `esp8266` > `2.0.0` > `tools` > `sdk` > `include`

**10** Open `user_interface.h` with a text editor

**11** Scroll down and before `#endif` add following lines:

`typedef void (*freedom_outside_cb_t)(uint8 status);`  
`int wifi_register_send_pkt_freedom_cb(freedom_outside_cb_t cb);`  
`void wifi_unregister_send_pkt_freedom_cb(void);`  
`int wifi_send_pkt_freedom(uint8 *buf, int len, bool sys_seq);`  

![screenshot of notepad, copy paste the right code](https://raw.githubusercontent.com/spacehuhn/esp8266_deauther/master/screenshots/notepad_screenshot_1.JPG)

**don't forget to save!**

**12** Go to the SDK_fix folder of this project

**13** Copy ESP8266Wi-Fi.cpp and ESP8266Wi-Fi.h

**14** Paste these files here `packages` > `esp8266` > `hardware` > `esp8266` > `2.0.0` > `libraries` > `ESP8266WiFi` > `src`

**15** Open `esp8266_deauther` > `esp8266_deauther.ino` in Arduino

**16** Select your ESP8266 board at `Tools` > `Board` and the right port at `Tools` > `Port`  
If no port shows up you may have to reinstall the drivers.

**17** Depending on your board you may have to adjust the `Tools` > `Board` > `Flash Frequency` and the `Tools` > `Board` > `Flash Size`. In my case i had to use a `80MHz` Flash Frequency, and a `4M (1M SPIFFS)` Flash Size

**18** Upload!

**Note:** If you use a 512kb version of the ESP8266, you need to comment out a part of the mac vendor list in data.h.

**Your ESP8266 Deauther is now ready!**