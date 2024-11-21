---
title: Portable Distance Sensor
date: 2024-11-18 00:00:00 +0300
categories: [IoT, Arduino]
tags: [Embedded Project, Electronics, LCD, HC-SR04, Power Supply, Battery Powered, Portable, Real-Time Data Display, Error Indication, Distance Meter]   
author: yarali 
published: true

---


## Introduction

As technology continues to evolve and shape our daily lives, tools that enhance convenience and precision are more important than ever. In this tutorial, we’ll explore how to create a portable distance detector using an Arduino, an HC-SR04 ultrasonic sensor, and an LCD display. The HC-SR04 is widely known for its ability to measure distances accurately and efficiently by emitting ultrasonic waves and calculating the time it takes for the echo to return.  
  
What sets this project apart is its practicality: by simply pressing a button, the device calculates and displays the distance between the sensor and an object in real-time. Along the way, we’ll also cover essential concepts like software debouncing to ensure accurate button presses and a moving average filter to smooth out distance readings for reliable results. Additionally, it includes an error indication system to alert you when the sensor fails to detect a valid distance, ensuring reliability in various scenarios. By the end of this guide, you’ll have a handy tool that demonstrates the power of Arduino for real-world applications.  


## Overview  

This project focuses on building a portable and user-friendly distance detection system which is designed to provide real-time measurements and display the results on an LCD. The system offers a user-friendly interface, allowing users to activate the device with a button press. It also includes an error indication for invalid readings, ensuring reliable performance in various environments. 


## Features  

**Real-Time Distance Measurement**  
 Accurately measures the distance between the sensor and an object using ultrasonic waves and displays the measured distance *instantly* on the LCD screen.  

**Button-Activated Operation**  
 The device operates at the press of a button, triggering the measurement and display of the distance, providing a simple and user-friendly interface.  

**Software Debouncing**  
 To eliminate false triggers from button presses, software debouncing ensures that only valid button actions are detected, enhancing the system's reliability.  

**Moving Average Filter**  
 The distance readings are smoothed using a moving average filter, which helps reduce fluctuations and noise, providing more accurate and stable measurements.  

**Error Indication**   
 The project includes an error indication system that alerts users when the sensor fails to provide a valid distance reading, ensuring reliable performance.  

**LCD Display**  
 A clear and easy-to-read LCD display shows the calculated distance in real-time, making it simple to monitor measurements.  

**Compact and Portable**  
 The system is designed to be compact and easily portable, allowing it to be used in a variety of environments.  


## Required Components  

Arduino Nano (for better portability)  
HC-SR04 Ultrasonic Distance Sensor  
16x2 LCD Display  
10k Potentiometer for LCD contrast adjustment  
Red LED for feedback  
330 Ohm Resistor (for LED)  
Push Button  
10k Ohm Resistor (for Pull-Up)  
Breadboard and Jumper Wires
9V Battery with breadboard power supply  
Arduino IDE (for coding and uploading to the board)  
Download LiquidCrystal Libraries  

## How to Download Libraries  

If you’re not familiar with downloading and installing libraries in the Arduino IDE, you can check out my  [Portable Humidity and Temperature Sensor](https://omaryarali.github.io/posts/Portable-Humidity-and-Temperature-Sensor/) for a comprehensive explanation.  Additionally, before getting started, unlike the temperature and humidity sensor, which we controled using the DHT11 library in our previous project, we will control the HC-SR04 sensor manually, without using any external libraries.
   






