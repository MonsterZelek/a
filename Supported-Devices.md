# Supported Devices

This software is written for the ESP8266. There are plenty of development boards available, all you need to do is choose one.  
The ESP8285, which is basically just an ESP8266 with embedded flash memory, is also supported.  
The ESP32 is **not** supported!  

**Here are some of the most used boards for this project**

- [DSTIKE Boards](#dstike-boards)
- [List of supplies](#list-of-supplies)
- [NodeMCU](#nodemcu)
- [Wemos D1 mini](#wemos-d1-mini)
- [Adafruit HUZZAH ESP8266](#adafruit-huzzah-esp8266)
- [WARNING - Fake Boards!](#warning---fake-boards)

## DSTIKE Boards
![PICTURE DSTIKE Deauther OLED Board](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/DSTIKE_Deauther_Board.jpg)

If you want to support the development of this project, you can buy one of the offical boards by DSTIKE (Travis Lin) on following sites:  
- [Tindie 🇨🇳 ](https://tindie.com/stores/lspoplove)  
- [AliExpress 🇨🇳 ](https://dstike.aliexpress.com/store/2996024)  
- [Taobao 🇨🇳 ](https://shop135375846.taobao.com)  
- [Maltronics 🇬🇧 ](https://maltronics.com/collections/deauthers)  

The Deauther boards come preflashed with the Deauther software and don't require the installation process.  
They are made especially for this project and come with a sharp 1.3 inch OLED screen, external antenna and 18650 battery connector. DSTIKE also offers a cheaper version without screen and a NodeMCU board. You can of course flash them with your own software and use them just like any other development board.  

## List of supplies
If you want to assemble the project yourself, you can find the parts you need [here](https://github.com/PwnKitteh/InsanelyCheapElectronics#deauther-20). We recommend the NodeMCU for this, and you can use either of the displays linked there. 

## NodeMCU
This is the recommended board for beginners that want to learn more about electronics and programming!  
![External PICTURE NodeMCU v1.0](https://raw.githubusercontent.com/spacehuhn/nodemcu-devkit-v1.0/master/Documents/NodeMCU_DEVKIT_1.0.jpg)  
The NodeMCU is an open source project and there are many companies producing it. The most known one is Amica. There is also a Lolin NodeMCU v3 but don't get confused by any version number:    


![PICTURE NodeMCU comparison](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/nodemcus.jpg)  


I always recommend the v1.0 (might be sold under a different version number). It's the board from Amica. It is cheap, breadboard friendly and uses the cp2102, a better alternative to the old CH340 USB to serial chip.  
Please note that the quality of those boards can vary a lot! They are produces very cheap and you can get them for around 3 - 5 USD from AliExpress and other Chinese based sellers. So don't pay too much for them!  

There is also this NodeMCU inspired development board by DSTIKE:  
https://www.tindie.com/products/lspoplove/nodemcu-07wifi-deauther-preflashed/  
It has a LiPo charger on-board and allows you to connect an external antenna for better range.  

## Wemos D1 mini
The Wemos boards have decent quality, are cheap and very small.  
They work just like a NodeMCU and you can get a variety of addon shields for them!  
But you have to be careful, there are a lot copies of the Wemos products!  

## Adafruit HUZZAH ESP8266
Adafruit has a Feather board with the ESP8266 in their sore. Those are a bit more pricy than the chinese NodeMCUs but you get a very quailty board in return, good online documentation and a friendly community around it.  

## WARNING - Fake Boards!

![Fake WEMOS Board 1](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/fake_wemos_1.jpg)
![Fake WEMOS Board 2](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/fake_wemos_2.jpg)

You will find some cheaper boards that look like the official deuther boards but for lower prices. **I highly recommend to stay away from them!**  
These companies like to copy Travis Lin's (DSTIKE) designs, use my software and sell it as seemingly official Wemos boards!  
Recently they started to label their boards as "TTGO". They don't put much effort into it, so the quality is often horrible and the PCB design very poor.  
**DON'T SUPPORT THIS BEHAVIOUR!**  This is not how open source works! It hurts not only this project, but the whole cummunity around it!  

Here are some of the biggest shops (mostly on AliExpress) you better stay away from:  
- LILY GO 
- FACE-TO-FACE Electronic
- Seatechnolgy

![Fake WEMOS Board 3](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/fake_wemos_3.jpg)
![Fake WEMOS Board 4](https://raw.githubusercontent.com/wiki/spacehuhn/esp8266_deauther/img/fake_wemos_4.jpg)