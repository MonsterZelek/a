## Installation Option 1

The only thing you will need is a computer and an ESP8266.  

I recommend you to buy a USB breakout/developer board, because they have 4Mb flash and are very simple to use.
It doesn’t matter which board you use, as long as it has an ESP8266 on it.  

### **Option 1** Uploading the bin files  

**Note:** the 512kb version won't have the full MAC vendor list.  
The NodeMCU and every other board which uses the ESP-12 has 4mb flash on it.

**0** Download the current release from [here](https://github.com/spacehuhn/esp8266_deauther/releases)  

**1** Upload using the ESP8266 flash tool of your choice. I recommend using the [nodemcu-flasher](https://github.com/nodemcu/nodemcu-flasher). If this doesn't work you can also use the official [esptool](https://github.com/espressif/esptool) from espressif.

**That's all! :)**

Make sure you select the right com-port, the right upload size of your ESP8266 and the right bin file.  

If flashing the bin files with a flash tool is not working, try flashing the esp8266 with the Arduino IDE as shown below.
