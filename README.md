Welcome To: LeoPhi Basic Example Firmware!!
================================

##### Note: This is for the LeoPhi Hardware Version 2 Branch

This is the base example sketch for using LeoPhi hardware. (Please note the branches for HWVer1 and 2) 
It outputs data via USB serial but can easily be modified to use Serial1 as well.

Reading pH just got a bit easier
-------------------------

With Arduino1.0.2 and up how the Leonardo is reset was changed and with the popularity of the LeoPhi platform I though it would be a good idea to update the hardware and bring the bootloader up to the newest version.

As before reading pH has never been easier, and with the new hardware version so it augmenting LeoPhi!
All Standard Leonardo pins are brought out via the Digital Header and Analog header!

Simply plug in LeoPhi via a USB port, point you favorite Serial Port monitor to LeoPhis port and off you go! 
**LeoPhi even works on openWRT flashed routers for pH readings over Wifi!**

Please see [LeoPhi's Project page](http://www.sparkyswidgets.com/portfolio-item/leophi-usb-arduino-ph-sensor/) for more information!
<http://www.sparkyswidgets.com/portfolio-item/leophi-usb-arduino-ph-sensor/>

Whats in the firmware?
-------------------------

**Note Even though the Oversampling works I have removed it for now for a few reasons, I will however create another sketch with oversample as the main focus** 
This sketch provides a good base to show how to use LeoPhi, and to provide an out of the box pH meter solution.
While it is rather basic in some aspects it also shows more advanced methods of manually calculating pH from an analog front end (see Hardware portion).
The sketch also shows how to implement oversampling of Arduino (AVR) ADCs using Timer4 and an ISR to create a fixed frequency sample rate. With the changes to Leonardo in newer Arduino's I shifted the oversampling over to timer4, this allows for PWM and other things to work in tandem with OS the ADC!

Installation Info
-------------------------

As of Arduino 1.0.4 I have started maintaining an Arduino branch with the Leo boards already included! I also keep this build fairly up to date with the latest changes when they don't break too many things :) I have builds for all 3 major OSes so please use the build for your perfered OS this is hte easiest way to support LeoPhi in your environment.
<https://github.com/SparkysWidgets/Arduino>

Basic Usage
-------------------------

Usage of LeoPhi is very easy, with on board USB a fully CDC compatible bootloader (modified leonardo) all you need to do is plug it in and send some serial commands! Send an S to calibrate to ph 7 solution, F to calibrate to 4 an R to read and etc...

There are 2 serial ports one for the USB and one is the hardware serial port(Tx,Rx), this makes it useful as a USB to serial converter as well, but also means that the proper port must be select for use in any project. For example a Raspberry pie could interface LeoPhi(careful on levels) over USB serial while the same data is dumped over the Hardware Serial to another Arduino. An I2C slave example code is also implemented which uses some of the same commands and shows how to easily implement a pH sensor with an I2C interface!

####Some of the commands are:
- C : Continuous Read Mode: Dump readings and data every second
- R : Single pH reading: response "pH: XX.XX" where XX.XX is the pH
- E : Exit continuous read mode
- S : set pH7 Calibration point
- F : set pH4 Calibration point: also recalcs probe slope and saves settings to EEPROM
- T : set pH10 Calibration point: also recalcs probe slope and saves settings to EEPROM 
- X : restore settings to default and ideal probe conditions

Hardware: Schematics and Layouts
-------------------------

- Take a look in [LeoPhi's Hardware Repo](https://github.com/SparkysWidgets/LeoPhiHW) for the EAGLE files!
- Check out my I2C pH interface[MinipH](http://www.sparkyswidgets.com/portfolio-item/miniph-i2c-ph-interface/) for a really cost effective PH Probe interface!


License Info
-------------------------

<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.en_US"><img alt="Creative Commons License" style="border-width: 0px;" src="http://i.creativecommons.org/l/by-sa/3.0/88x31.png" /></a><br />
<span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">LeoPhi</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="www.sparkyswidgets.com" property="cc:attributionName" rel="cc:attributionURL">Ryan Edwards, Sparky's Widgets</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.en_US">Creative Commons Attribution-ShareAlike 3.0 Unported License</a>.<br />
Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="portfolio-item/leophi-usb-arduino-ph-sensor/" rel="dct:source">http://www.sparkyswidgets.com/portfolio-item/leophi-usb-arduino-ph-sensor/</a>