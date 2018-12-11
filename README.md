# Build Instructions for Raspberry Pi L3GD20H Gyroscope

## Table of Contents
1. [Introduction](#introduction)
2. [Materials and Budget](#materials-and-budget)
3. [Raspberry Pi Configuration](#raspberry-pi-configuration)
4. [Mechanical Assembly and Soldering](#mechanical-assembly-and-soldering)
5. [Power Up](#power-up)
6. [Schedule](#schedule)

### Introduction
gyroscope is a type of sensor that can sense twisting and turning motions. The gyposcope is a triple axis gyro.  The board can change  the sense see it can be more easy for process, scale from 250, 500 or 2000. Gyroscope catch motion if it get moved around and the user can tell how is it moving. The chip uses 3.3v max, it is mainly use with Arduino boards but it can be use on the raspberry pi first.

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/IMG_20181118_235344.jpg" width="300">

### Materials and Budget
The total budget will cost you around CAD$186.5 not including tax and shipping. The price will vary depending on your location

* [Raspberry Pi 3 Kit](https://www.amazon.ca/CanaKit-Raspberry-Complete-Starter-Kit/dp/B01CCF6V3A/ref=sr_1_5?s=pc&ie=UTF8&qid=1516324581&sr=1-5&keywords=Raspberry+Pi+3) - CAD$99.99
* [L3GD20H Gyro](https://www.adafruit.com/product/1032) - USD$12.50
* [9 Pin Receptacle Socket](https://www.creatroninc.com/product/9-pin-receptacle-socket/) - CAD$0.50
* [40 Pin (20X2) Dual Row Receptacle Socket](https://www.creatroninc.com/product/40-pin-20x2-dual-row-receptacle-socket/) - CAD$2.25
* Custom PCB, [try](http://www.custompcb.com/) about USD$50 or any other pcb maker. [Gerbers file](https://github.com/chenken12/L3GD20H-gyroscope/tree/master/L3GD20H%20-%20Frizting)
* [Enclosure](https://github.com/chenken12/L3GD20H-gyroscope/blob/master/Pi2CaseX6%20-%20Kenneth%20x16.cdr) used a 1/8 inch acrylic sheet around 6 x 7 inch

Equipments
* Soldering Station
* Soldering wire
* Safety Glasses
* Anti-Static Wrist Strap

### Raspberry Pi Configuration
Dowload these 3 items to setup your raspberry [image](https://github.com/six0four/StudentSenseHat/blob/master/cribpisdcard.md):
* https://www.sdcard.org/downloads/formatter_4/index.html
* http://downloads.raspberrypi.org/raspbian/images/raspbian-2018-06-29/2018-06-27-raspbian-stretch.zip
* http://www.alanlay.com/blog/2014/6/8/raspberry-pi

### Mechanical Assembly and Soldering
1. Break the break_away pin into 9 pin set. Then start by soldering the sensor to the pins of the header. The 4 main pin that needs to be solder is the Vin, GND, SCL, SDA

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/IMG_20181108_171753.jpg" width="300">

2. This is the design for my [PCB](https://github.com/chenken12/L3GD20H-gyroscope/tree/master/L3GD20H%20-%20Frizting) using [Fritzing software](http://fritzing.org/download/) 

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/gyro_pcb.png" width="300"><img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/gyro_schem.png" width="300">

##### Pins used
* Vin - power pin
* GND - ground
* SCL - i2c pin
* SDA - i2c pin

3. Now solder the PCB the following:
* Via (need a  wire to pass though the hole)
* 20x2 - pin socket
* 7-pin socket 

This is the spots where I soldered the pin to

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/IMG_20181106_173529.jpg" width="300"><img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/IMG_20181106_173522.jpg" width="300">

### Power Up
1. power up your pi to see if the raspberry load, if not redo the [Raspberry Pi Configuration](#raspberry-pi-configuration)
2. open the terminal and detecting the sensor with this command
```
sudo i2cdetect -y 1
```
This will display an output of the sensor's address - 0x6B

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/IMG_20181024_004159.jpg" width="300">

3. To test if your sensor can read data, python code [here](https://github.com/chenken12/L3GD20H-gyroscope/blob/master/gyro.py). Run theis program in the terminal
```
python gyro.py
```
Here is a sample output:

<img src="https://raw.githubusercontent.com/chenken12/L3GD20H-gyroscope/master/images/gyro_xyz_data.png" width="300">

### Schedule
How long does it that to build?
Download all the software can take between 30min to 2 hour
* Download the software beforehand to save you sometime

Loading image to sd card and setup the pi take up to 1 to 1.5 hour <br>
Soldering can be as fast as 30 min to 1 hour <br>
Other is waiting on the parts to come.
