## FAQ

**I can't find any WiFi networks!?!?**

Make sure there are 2.4ghz networks in your area. This device will not find any 5ghz devices

**I can't remember my WiFi name or password**

Plug your device into your computer and log the device's output. It will display the SSID name along with the password

**I am getting errors when trying to with the arduino software?**

Make sure you have extracted the ZIP file that you have downloaded from this GitHub page

**How do I edit the HTML CSS and JS?**

**1** open minifier.html  
**2** paste the html code in the upper textfield  
**3** click on `minifiy + byte-ify`  
**4** copy the results  
**5** go to data.h and replace the array (of the changed html file) with the copied bytes  

now compile and upload your new sketch :)

**Could it auto-deauth all APs in the range?**

Yes, but I will not implement this 'feature' for ethical and legal reasons.

**Can it sniff handshakes?**

The ESP8266 has a promiscuous mode in which you can sniff packets, but handshake packets are dropped and there is no other way to get them with the functions provided by the SDK.  
Maybe someone will find a way around this barrier in the future.

**espcomm_sync failed/espcomm_open when uploading**

The ESP upload tool can't communicate with the chip, make sure the right port is selected!  
You can also try out different USB ports and cables.  
If this doesn't solve it you may have to install USB drivers.  
Which drivers you need depends on the board, most boards use a cp2102 or ch340.

**AP scan doesn't work**

There is a reported issue on this: https://github.com/spacehuhn/esp8266_deauther/issues/5  
Try switching the browser or opening the website with another device.   

**Deauth attack won't work**

If you see 0 pkts/s on the website then you've made a mistake. Check that you have followed the the installation steps correctly and that the right SDK installed, it must be version 2.0.0!
If it can send packets but your target doesn't loose its connection, then the Wi-Fi router either uses [802.11w](#how-to-protect-against-it) and it's protected against such attacks, or it communicates on the 5GHz band, which the ESP8266 doesn't support because of its 2.4GHz antenna.

### If you have other questions or problems with the ESP8266 you can also check out the official [community forum](http://www.esp8266.com/).