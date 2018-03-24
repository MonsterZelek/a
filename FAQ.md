# FAQ
**Overview**
- [5GHz Support](#5ghz-support)
- [ESP32 and ESP8285 Support](#esp32-and-esp8285-support)
- [Difference between Jammer and Deauther](#difference-between-jammer-and-deauther)

## 5GHz Support
The ESP8266 supports 2.4GHz WiFi, which is already very impressive if you think about how small, powerful, accessible and affordable this system on a chip is.  
However, a lot of people asked for 5GHz support because of this project but is not able to do that.  
As of right now (early 2018) no hackable 5GHz SoC is available in the form of something like the ESP8266.  
Even if someone would make such a chip, it would be incompatible with this software.  
You could build a dual band Deauther with a Raspberry Pi and the right WiFi module.  
But as of right now, it's not always easy to find good Dual-Band WiFi chips that support packet injection and monitor mode.  

> THE ESP8266 DOES NOT AND WILL NOT SUPPORT 5GHZ

Those that support it are often expensive and need special drivers (this will change in the future as new chips are released all the time).  
But if you want to try it, look for the `rtl8812au` or `rtl8811au` WiFi modules. Those have already been used to inject packets on 5GHz.  

# ESP32 And ESP8285 Support
ESP32: No  
ESP8285: Yes  
See [Supported Devices](https://github.com/spacehuhn/esp8266_deauther/wiki/Supported-Devices) for more.  

# Difference between Jammer and Deauther
While a jammer just creates noise on a specific frequency range (i.e. 2.4GHz), a deauthentication attack is only possible due to a vulnerability in the WiFi (802.11) standard. The deauther does not interfer with any frequencies, it is just sending a few WiFi packets that let certain devices disconnect. That enables you to specifically select every target. A jammer just blocks everything within a radius and is therefore highly illegal to use.  

Watch this video for a good explanation on the technical and legal differences: [WiFi Jammers vs Deauthers | What's The Difference?](https://www.youtube.com/watch?v=6m2vY2HXU60)  