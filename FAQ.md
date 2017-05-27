**I can't find any WiFi networks**

Make sure there are 2.4ghz networks in your area. This device will not find any 5ghz networks!  

**I can't remember the WiFi name or password**

Plug your device into your computer and open the serial monitor of Arduino. Set the baudrate to 115200 and press reset on your board. It will display the SSID name along with the password.  

**How do I reset it?**

Method 1: Connect pin 4 (D2 on the NodeMCU) to GND and plug the device in.  
Method 2: Connect your device, open up the serial monitor in Arduino, change the baudrate to 115200, type in "reset" and click send.  

**I am getting errors when trying to with the Arduino**

Make sure you have extracted the ZIP file that you have downloaded from this GitHub page.
Also follow the steps carefully and make sure to select the right settings in the board selection.  

**How do I edit the HTML CSS and JS?**

**1** Use a minifier (e.g. htmlcompressor.com) to get your files as small as possible  
**2** Open converter.html  
**3** Paste the code in the left textfield  
**4** Press Convert  
**5** Copy the results from the right textfield  
**6** Go to data.h and replace the array of the changed file with the copied bytes  

Now compile and upload your new sketch :)

**Could it auto-deauth all APs in the range?**

Yes, but I will never implement this 'feature' for ethical and legal reasons!  

**Can it sniff handshakes?**

The ESP8266 has a promiscuous mode in which you can sniff packets, but you can't get the complete packet and there is no other way to get them with the functions provided by the SDK.  

**espcomm_sync failed/espcomm_open when uploading**

The ESP upload tool can't communicate with the chip, make sure the right port is selected!  
You can also try out different USB ports and cables.  
If this doesn't solve it, you may have to install USB drivers.  
Which drivers you need depends on the board. Most boards use a cp2102 or CH340G.  

**I loose the connection when scanning for stations/client cevices**

That is normal and there is no other way. The chip has to turn off its access point to sniff for all packets nearby.  

**I loose the connection when starting an attack**

That might happen because of an channel change of the ESPs access point. When you have the same channel setup in settings as the AP you're attacking, you won't loose the connection.  

**Deauth attack won't work**

If you used Arduino to flash it and you see 0 pkts/s on the website then you've made a mistake. Check that you have followed the the installation steps correctly and that the right SDK installed, it must be version 2.0.0!
If it can send packets but your target doesn't loose its connection, then the Wi-Fi router either uses [802.11w](#how-to-protect-against-it) and it's protected against such attacks, or it communicates on the 5GHz band, which the ESP8266 doesn't support.
Also note that some devices reconnect faster than it's deauthenticating them, so it will not block the connection completly, but slowing it down.  

**How do I clear the EPROM**

Have a look at this project: https://github.com/schinfo/EEPROM-Cleaner  

**What is the Probe-Request attack for?**

Probe-Requests are packets sent out by unconnected Wi-Fi devices to actively search for known networks.  
There are commercial trackers available to scan for these packets and analyse them.
Some shops use such systems to get more information about their costumers.  
The Probe-Request attack is a great way to confuse these systems.

### If you have other questions or problems with the ESP8266 you can also check out the official [community forum](http://www.esp8266.com/).