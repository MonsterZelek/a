# Development

This is a collection of useful descriptions on how to change specific things in the code.  
It's made for people with experience in coding to help navigate through the code.  

**Overview**
- [Adding support for different displays](#adding-support-for-different-displays)
- [Adding a setting](#adding-a-setting)
- [Adding serial CLI command](#adding-serial-cli-command)
- [Customizing the web GUI](#customizing-the-web-gui)

## Adding support for different displays
If you want to port the diplay code onto something different than the SSD1306 and SH1106 OLEDs that this software was written for, we recommend making a fork of the project and a new issue to let people know what you're working on.  
In `DisplayUI.cpp` and `Display.h` are a lot of sections marked with `// ===== adjustable ===== //`, those are especially for you. Depending on your screen, you might have to change other code as well and add a few `#define`s to the `0_config.h`.  
I hope these tips help! It's hard to say what you exactly need to do, because every display and its library works differently.  

## Adding a setting
To add new custom setting you have to modify a few files:  

- Add the variable definition in `Settings.h` under `private`:  
```
String mySetting = "someDefaultValue";
```

- Add the name of the setting in `language.h`:  
```
static const char S_MYSETTING[] PROGMEM = "mySetting";                   // mySetting`.  
```

- Add a getter and setter in `Settings.h` under `public:`:  
```
String getMySetting();
```
```
void setMySetting(String mySetting);
```  

- Program the getter and setter in `Settings.cpp`:  
```
String Settings::getMySetting(){ 
    return mySetting; 
}
```
```
void Settings::setMySetting(String mySetting){
    Settings::mySetting = mySetting;
    changed = true;
}
``` 

- Add your setting to the `load` function in `Settings.cpp`:  
```
if(data.containsKey(keyword(S_MYSETTING))) setMySetting(data.get<String>(keyword(S_MYSETTING)));
```

- Add your setting to the `reset` function in `Settings.cpp`:  
```
setMySetting("someDefaultValue");
```

- Add your setting to the `getJsonStr` function in `Settings.cpp`:  
```
data.set(getKeyword(S_MYSETTING), mySetting);
```

- Add your setting to the `set` function in `Settings.cpp`:  
```
else if (eqls(str,S_MYSETTING)) setMySetting(value);
```

- Add your setting to the `get` function in `Settings.cpp`:  
```
else if (eqls(str,S_MYSETTING)) return getMySetting();
```

- Now compile and upload and run the `get settings` command to see if your new setting was successfully added. 

- Add your new Setting to the [`settings.md`](https://github.com/spacehuhn/esp8266_deauther/master/settings.md) file with a short description.

- Add you setting description to the [`lang/en.lang`](https://github.com/spacehuhn/esp8266_deauther/master/web_interface/lang/en.lang) file.  

## Adding serial CLI command

I can't explain the whole code and what every function does, but here is a basic example of how to add a command that turns the display on and off.  

- In `language.h` and add a string for your command and parameters:  

```
static const char CLI_SCREEN[] PROGMEM = "screen";
static const char CLI_ON[] PROGMEM = "on";
static const char CLI_OFF[] PROGMEM = "off";
```

- Go to `SerialInterface.cpp` and in the bottom of the file, add an `else if` statement between the last command and `// ===== NOT FOUND ===== //`:  

```
// screen <on/off>
else if(eqlsCMD(0, CLI_SCREEN) && (eqlsCMD(1,CLI_ON) || eqlsCMD(1,CLI_OFF))){
  if(eqlsCMD(1,CLI_ON)){
    displayUI.on();
  } else if(eqlsCMD(1,CLI_OFF)){
    displayUI.off();
  }
}
```
- Upload and test your command

- Add the full command string to `language.h`:  

```
static const char CLI_HELP_SCREEN_ON[] PROGMEM = "screen <on/off>";
```

- Add your command string to the help command in `SerialInterface.cpp`:  
```
  // ===== HELP ===== //
  if (eqlsCMD(0, CLI_HELP)) {
    ...
    prntln(CLI_HELP_SCREEN_ON);
    ...
  }
```

- Add your command to the [`serialcommands.md`](https://github.com/spacehuhn/esp8266_deauther/master/settings.md) file.  




## Customizing the Web GUI

When customizing the Web GUI, keep in mind the path limit in SPIFFS is 32 chars or you will get puzzling situations.
In order to avoid that you should not create unnecessarily deep folder structure or use long filenames, as it'll add to the length and will eventually get truncated.

