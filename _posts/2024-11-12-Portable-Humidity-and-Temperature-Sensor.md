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

### Temperature Sensing Component    

For temperature sensing part, DHT11 uses a thermistor to measure temperature. In a thermistor, electrical resistance changes with temperature due to increased thermal energy affecting the motion of charge carriers (like electrons). At higher temperatures, more charge carriers become available to move, resulting in lower resistance. 

 Thermistors are usually made of semiconductor materials. In semiconductors, the number of charge carriers increases with temperature as more electrons gain enough energy to jump into the conduction band from the valance band. This causes the thermistor’s resistance to decrease.     

 They are small, durable and sensitive at low temperature. Thermistors have moderate temperature range (up to 150°C) and low-to-moderate cost (depending on accuracy). DHT11 is a low-cost device and the sensor reading can be up to 2 seconds. It is less accurate compared to more advanced sensors like the DHT22 or others that can measure over a wider temperature range with higher precision. It measures temperature with a Negative Temperature Coefficient (NTC) thermistor in which resistance is negatively correlated with temperature. The graph in the image shows the relationship between temperature and resistance in an NTC thermistor. As the temperature rises, the resistance decreases, allowing the sensor to measure changes in temperature.  

 Then the DHT sensor's internal microcontroller reads the change in resistance and converts it into a temperature value using pre-defined calibration data and equations specific to the thermistor’s material properties.  


### Humidity Sensing Component  

The DHT sensor has a capacitive humidity sensor that consists of two electrodes with a moisture-absorbing substrate (usually a polymer) between them.  Capacitance is a property that indicates how much electric charge a capacitor can store for a given electric potential. It depends on the area of the plates, the distance between them, and the dielectric constant (a material property related to its ability to store electric energy) of the medium between the plates.  

 This polymer can absorb water vapor from the surrounding air. When the moisture level in the air (humidity) changes, water molecules (which are polar, meaning they have a partial electric charge) are absorbed by the polymer. Water has a high dielectric constant compared to air, so when it is absorbed into the polymer, the dielectric constant between the capacitor plates increases. The increased dielectric constant causes the capacitance to increase. By measuring this change, the DHT sensor can infer the relative humidity of the surrounding air.

### Bonus Information: The Role of Polarity in Water Molecules  

 *Being polar* means that the molecule has a partial electric charge on different ends due to the distribution of electrons. Water molecules consist of one oxygen atom and two hydrogen atoms. Oxygen is more electronegative than hydrogen, meaning it pulls electrons toward itself. This creates a negative charge near the oxygen atom and a positive charge near the hydrogen atoms, making the molecule have a dipole — a positive side and a negative side.

 This polarity is what allows water to interact strongly with other polar substances and affects the way it behaves in various environments, including its ability to increase the dielectric constant in materials like polymers when absorbed. The increased dielectric constant helps enhance the capacitor's ability to store electrical charge.  



## Data Communication Protocol of the DHT11 Sensor

Now that we've explored the internal structure of the DHT11, let's delve into how the sensor communicates with external devices, specifically through its data transmission protocol. After measuring capacitance and resistance, the sensor’s microcontroller (integrated circuit or IC) uses these analog values to calculate temperature and humidity digitally. The DHT11 uses a unique single-wire communication protocol, which allows it to send temperature and humidity data over a single digital pin. 

### Single-Wire  Communication Protocol Explained

The DHT11 sensor communicates using a single-wire protocol, where voltage levels and timing define logic HIGH (1) and logic LOW (0) states. The communication process consists of three main steps: first, the microcontroller sends a request signal to the DHT11. Next, the sensor responds with a response signal. Finally, it transmits 40 bits of data containing temperature and humidity readings.

Images are taken from ElectronicWings.  

![](assets/3_Start_Pulse.jpg) 



  




