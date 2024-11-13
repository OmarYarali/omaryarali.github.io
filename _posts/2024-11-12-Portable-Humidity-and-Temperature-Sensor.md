---
title: Portable Humidity and Temperature Sensor
date: 2024-11-12 00:00:00 +0300
categories: [IoT, Arduino]
tags: [Embedded Project, Electronics, LCD, DHT, Power Supply, Battery Powered, Portable, Real-Time Data Display, Error Indication]   
author: yarali 
published: true

---


## Introduction

In our increasingly connected world, monitoring environmental conditions like temperature and humidity has become essential in everything from weather stations to smart home systems. In this tutorial, we'll walk through creating a temperature and humidity monitoring setup using an Arduino, a DHT11 sensor, and an LCD display. The DHT11 is a popular sensor for these measurements due to its accuracy, affordability, and compatibility with Arduino. By the end of this guide, you'll have a functioning setup that can display real-time data, helping you get one step closer to understanding and controlling your environment.


## Overview

This project is a compact, portable temperature and humidity monitoring system built with Arduino, designed to provide real-time data on an LCD display and alert users with a red LED indicator when values are unreadable. Ideal for learners who are interested in environmental sensing, this setup combines portability with ease of use. The system includes a DHT sensor module for accurate temperature and humidity readings, an LCD for clear data display, a red LED to indicate sensor errors, and a small rechargeable battery for enhanced mobility. 


## Features

**Real-time Temperature and Humidity Monitoring**  
Continuously displays accurate temperature and humidity readings from the DHT11 sensor on a 16x2 LCD screen, updated every few seconds. This display allows users to monitor environmental changes instantly, making it ideal for portable weather stations, greenhouse monitoring, and DIY environmental sensing projects.

**Error Indication with Red LED**  
A built-in red LED signals the user when sensor data is unreadable, such as when the sensor encounters an error or is disconnected. This feature ensures the user is immediately aware of issues, providing a reliable way to identify and troubleshoot potential problems in real time.

**Adjustable LCD Contrast**  
Includes a 10k potentiometer to adjust the contrast of the 16x2 LCD screen, improving display visibility in various lighting conditions. This feature is especially useful when using the sensor outdoors or in different ambient lighting.

**Portable Power Supply**     
Powered by a 9V battery connected through a breadboard power supply module, making it easy to take the device anywhere without the need for a direct power source. The portable design supports long-term use, ideal for mobile applications or places without stable power access.



## Required Components

Arduino Nano (for better portability)     
DHT11 Temperature and Humidity Sensor  
16x2 LCD Display  
Red LED for error indication  
10k Potentiometer for LCD contrast adjustment  
10k Resistor (for DHT11)  
330 Ohm Resistor (for LED)  
Breadboard and jumper wires  
9V Battery with breadboard power supply  
Download DHT and LiquidCrystal Libraries


## How to Download Libraries

You can easily access and install most libraries directly from the Arduino IDE. Simply open the Library Manager by going to Sketch > Include Library > Manage Libraries or use the shortcut Ctrl + Shift + I (Windows) or Cmd + Shift + I (Mac). In the Library Manager, you can search for the library you need, such as DHT(by Adafruit), and then click Install next to it. Libraries which are already built into the IDE, like LiquidCrystal, are ready to use without installation—just include them in your code with:  
 ```c
 #include <LiquidCrystal.h>  
```
 This makes it quick and simple to add functionality to your projects.  



## How DHT11 Sensor work?

![](assets/DHT11 Sensor Internal Structure.jpg) 

This image shows the internal structure and working principle of the DHT11 sensor, which is used for measuring temperature and humidity. The image provides details on the two main components of the DHT11 sensor: the temperature sensing component and the humidity sensing component.

## Temperature Sensing Component


