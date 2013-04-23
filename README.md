Welcome To: LeoPhi Basic Example Firmware!!
================================

##### Note: This is for the LeoPhi Hardware Version 1 Branch

This is the base example sketch for using LeoPhi hardware. (Please note the branches for HWVer1 and 2) It outputs data via USB serial but can easily be modified to use Serial1 as well.

Reading pH just got a bit easier
-------------------------

With recent updates to the firmware reading pH has never been easier. Simply plug in LeoPhi via a USB port, point you favorite Serial Port monitor to LeoPhis port and off you go! **LeoPhi even works on openWRT flashed routers for pH readings over Wifi!**

Please see [LeoPhi's Project page](http://www.sparkyswidgets.com/Projects/LeoPhi.aspx) for more information!
<http://www.sparkyswidgets.com/Projects/LeoPhi.aspx>

Whats in the firmware?
-------------------------

This sketch provides a good base to show how to use LeoPhi, and to provide an out of the box pH meter solution.
While it is rather basic in some aspects it also shows more advanced methods of manually calculating pH from an analog front end (see Hardware portion).
The sketch also shows how to implement oversampling of Arduino (AVR) ADCs using Timer1 and an ISR to create a fixed frequency sample rate.

Installation Info
-------------------------

While LeoPhi is fully Arduino compatible it does require some installation to work fully With Arduino IDE.
##### Some of the changes needed (pretty standard to adding variants to Arduino) 
- if on windows LeoPhi.inf must be added to hardware/drivers folder
- Boards.txt must be modified with a LeoPhi board type section 
- Some Core files will need to be appended
- a LeoPhi variant is needed

Luckily we have a basic package with these changes [here](http://www.sparkyswidgets.com/Portals/0/LeoPhiSetup.zip).
**Even better see my Arduino Fork where I keep these changes up to date with the newest versions of Arduino!**
<https://github.com/SparkysWidgets/Arduino>

Basic Usage
-------------------------

Usage of LeoPhi is very easy, with on board USB a fully CDC compabtible bootloader (modified leonardo) all you need to do is plug it in and send some serial commands! Send an S to calibrate to ph 7 solution, F to calibrate to 4 an R to read and etc...

There are 2 serial ports one for the USB and one is the hardware serial port(Tx,Rx), this makes it useful as a USB to serial converter as well, but also means that the proper port must be select for use in any project. For example a Raspberry pie could interface LeoPhi(carefull on levels) over USB serial while the same data is dumped over the Hardware Serial to another Arduino. An I2C slave example code is also implemented which uses some of the same commands and shows how to easily implement a pH sensor with an I2C interface!

####Some of the commands are:
- C : Continous Read Mode: Dump readings and data every second
- R : Single pH reading: response "pH: XX.XX" where XX.XX is the pH
- E : Exit continous read mode
- S : set pH7 Calibration point
- F : set pH4 Calibration point: also relalcs probe slope and saves settings to EEPROM
- T : set pH10 Calibration point: also recalcs probe slope and saves settings to EEPROM 
- X : restore settings to default and idela probe conditions

Hardware: Schematics and Layouts
-------------------------

- Take a look in [LeoPhi's Hardware Repo](https://github.com/SparkysWidgets/LeoPhiHW) for the EAGLE files!
- Check out my I2C pH interface[MinipH](http://www.sparkyswidgets.com/Projects/MinipH.aspx) for a really cost effective PH Probe interface!
