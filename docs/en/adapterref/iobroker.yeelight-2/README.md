![Logo](admin/yeelight.png)

![Number of Installations](http://iobroker.live/badges/yeelight-2-installed.svg)
![Number of Installations](http://iobroker.live/badges/yeelight-2-stable.svg)
[![NPM version](http://img.shields.io/npm/v/iobroker.yeelight-2.svg)](https://www.npmjs.com/package/iobroker.yeelight-2)

![Test and Release](https://github.com/iobroker-community-adapters/ioBroker.yeelight-2/workflows/Test%20and%20Release/badge.svg)
[![Translation status](https://weblate.iobroker.net/widgets/adapters/-/yeelight-2/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)
[![Downloads](https://img.shields.io/npm/dm/iobroker.yeelight-2.svg)](https://www.npmjs.com/package/iobroker.yeelight-2)

**This adapter uses Sentry libraries to automatically report exceptions and code errors to the developers.** For more details and for information how to disable the error reporting see [Sentry-Plugin Documentation](https://github.com/ioBroker/plugin-sentry#plugin-sentry)! Sentry reporting is used starting with js-controller 3.0.

# ioBroker.yeelight-2

[Deutsche Beschreibung hier](README_de.md)

This adapter control your Yeelight device. this adapter is only for admin3. Admin2 is not supported

## Jump Version
When changing from the 0.4.X to the 0.9.X or higher, the objects must be deleted manually so they can be recreated.

## Installation
for RGB Bulbs you have to enable the LAN in the settings of the yeelight app.

![](admin/lan.jpg)

## Config
you can add manually devices or find devices in network. the basic port is 55443. if you want, you can change the name, ip, port and smartname

### smartname
if you type in a smartname, the device is add to the iobroker.cloud and can control by alexa. 

### Find device
with this button you can scan your Network for devices, if something is found, the divices added to the table. It takes about 20 seconds to scan the network. if the devices not found, the Lan mode is not enabled or the bulbs are in a nother network.

### Device not in the list
If your Device is not in the list eg. yltd003 use a different lamp with the same fetures in ths case desklamp or Color or something else.
## set_scene
Usage: This method is used to set the smart LED directly to specified state. If
the smart LED is off, then it will turn on the smart LED firstly and then apply the specified
command.

Parameters: 3 ~ 4.

 "class" can be "color", "hsv", "ct", "cf", "auto_dealy_off".

- "color" means change the smart LED to specified color and
brightness.
- "hsv" means change the smart LED to specified color and brightness.
- "ct" means change the smart LED to specified ct and brightness.
- "cf" means start a color flow in specified fashion.
- "auto_delay_off" means turn on the smart LED to specified
brightness and start a sleep timer to turn off the light after the specified minutes.

 "val1", "val2", "val3" are class specific.

Request Example: 
- ``["color", 65280, 70]``
- ``["hsv", 300, 70, 100]``
- ``["ct", 5400, 100]``
- ``["cf",0,0,"500,1,255,100,1000,1,16776960,70"]``
- ``["auto_delay_off", 50, 5]``

NOTE: Accepted on both "on" and "off" state.

 For above examples:

 - The first is to set color to "652280" and 70% brightness.
 - The second is to set color to Hue:300, Saturation:70 and max brightness.
 - The third is set CT to 500K and 100% brightness.
 - The forth one is to start a infinite color flow on two flow tuples.
 - The fifth one is turn on the light to 50% brightness and then turn off
after 5 minutes.

## Changelog
<!--
    Placeholder for the next version (at the beginning of the line):
    ### **WORK IN PROGRESS**
-->
### 1.3.1 (2024-02-15)
- (mcm1957) BREAKING: adapter requires node.js 18 or newer now.
- (Black-Thunder) Crashes at startup of adapter have been fixed. [#271, #227 and #222]
- (mcm1957) Testing has been changed to support node 18 and 20
- (mcm1957) Dependencies have been updated
- (Apollon77) make sure reconnects work correctly

### 1.2.1 (2022-06-16)
* (Apollon77) register error handler for Yeelight instance
* (Apollon77) Prevent to register too many event listeners on discovery
* (Apollon77) Set some states after object creation
* (Apollon77) Prevent some crash cases reported by Sentry

### 1.2.0 (2022-04-13)
* (Apollon77) Optimize unload handling and async executions
* (Apollon77) Prevent log on unexpected types
* (Apollon77) Add Sentry for crash reporting

### 1.1.2 (2021-08-05)
* Fix Joi Error

### 1.1.1 (2021-08-03)
* (MeisterTR) js-controller 3.3 fixes
* (jlssmt) fixed unhandled promise rejection causing the adapter to stop
* (jlssmt) adapter won't set power of offline devices to off anymore

### 1.1.0 (2021-07-26)
* (MeisterTR) add release-script update testing and dependencies
* (Diginix) fixed data types

### 1.0.3 (2019-12-01)
* (MeisterTR) add Pedant
* (MeisterTR) transfer to community

### 1.0.1 (2018-12-08)
* (MeisterTR) push version, added set_scene

### 0.9.6 (2018-12-08)
* (MeisterTR) yeelight-wifi added
* (MeisterTR) fixed  bugs
* (MeisterTR) add manuell light
* (MeisterTR) better error handling
* (MeisterTR) fixed reconnect at start
* (MeisterTR) delete object and smartname bug fixed

### 0.9.1 (2018-10-31)
* (MeisterTR) added offline detection, poll sates, cleanup

### 0.9.0 (2018-08-29)
* (MeisterTR) rebuild

### 0.4.1 (2018-08-29)
* (MeisterTR) fixed JSON error

### 0.4.0 (2018-08-29)
* (MeisterTR) fixed errors
* (MeisterTR) added scenen

### 0.3.6 (2018-07-07)
* (MeisterTR) catch spaces in config, small performance changes

### 0.3.5 (2018-06-18)
* (MeisterTR) added yeelight650, fixed some bugs, power on when ct change

### 0.2.9 (2018-06-07)
* (MeisterTR) change name for repo and npm

### 0.2.8 (2018-06-01)
* (MeisterTR) fixed bug wit port, fixed set ct by alexa

### 0.2.6 (2018-05-31)
* (MeisterTR) fixed manny bugs.

### 0.2.0 (2018-03-07)
* (MeisterTR) many changes add smartname Option, add manual devices, many fixes
* (MeisterTR) fix role for alexa

### 0.1.1 (2018-03-07)
* (MeisterTR)return to default value when turn on
* (MeisterTR)fix role for alexa

### 0.1.0 (2018-03-07)
* (MeisterTR) many changes, add hue and sat for alexa control

### 0.0.2 (2018-03-07)
* (MeisterTR) objects not overwirte after restart

### 0.0.2 (2018-03-07)
* (MeisterTR) testing added, log changed

### 0.0.1 (2018-01-29)
* (cahek2202) initinal version



base from: adb backup https://github.com/cahek2202/ioBroker.yeelight

## License
The MIT License (MIT)

Copyright (c) 2024 iobroker-community-adapters <iobroker-community-adapters@gmx.de>  
Copyright (c) 2018-2024 MeisterTR <meistertr.smarthome@gmail.com>, cahek2202 <cahek2202@mail.ru>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
