### Adding OLED display

![image of the esp8266 deauther with an OLED and three buttons](https://raw.githubusercontent.com/spacehuhn/esp8266_deauther/master/screenshots/esp8266_with_oled.jpg)

**0** Follow the steps [above](#compiling-the-source-with-arduino) to get your Arduino environment ready.

**1** Install this OLED driver library: https://github.com/squix78/esp8266-oled-ssd1306

**2** Customize the code for your wiring.  
		In `esp8266_deauther.ino` uncomment `#define USE_DISPLAY`.  
		Then scroll down and customize these lines depending on your setup.  
		I used a Wemos d1 mini with a SSD1306 128x64 OLED and 3 push buttons.  

		  //include the library you need
		  #include "SSD1306.h"
		  //#include "SH1106.h"

		  //button pins
		  #define upBtn D6
		  #define downBtn D7
		  #define selectBtn D5

		  #define buttonDelay 180 //delay in ms
		  
		  //render settings
		  #define fontSize 8
		  #define rowsPerSite 8

		  //create display(Adr, SDA-pin, SCL-pin)
		  SSD1306 display(0x3c, D2, D1);
		  //SH1106 display(0x3c, D2, D1);