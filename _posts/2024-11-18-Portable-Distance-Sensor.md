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
10k Ohm Resistor (Between Echo and Ground pin)  
16x2 LCD Display  
10k Potentiometer for LCD contrast adjustment  
Red LED for feedback  
330 Ohm Resistor (for LED)  
Push Button  
10k Ohm Resistor (for Pull-Up)  
Breadboard and Jumper Wires
External Power Supply 
Arduino IDE (for coding and uploading to the board)  
Download LiquidCrystal Libraries  

## How to Download Libraries  

If you’re not familiar with downloading and installing libraries in the Arduino IDE, you can check out my  [Portable Humidity and Temperature Sensor](https://omaryarali.github.io/posts/Portable-Humidity-and-Temperature-Sensor/) for a comprehensive explanation.  Additionally, before getting started, unlike the temperature and humidity sensor, which we controlled using the DHT11 library in our previous project, we will control the HC-SR04 sensor manually, without using any external libraries.  

## How HC-SR04 ultrasonic sensor works?    

Images are taken from element14 presents.    
        
Before diving into how ultrasonic sensors work, let's first understand ultrasonic sound.    

### What is Ultrasonic Sound?  

Sound is a vibration that travels through a medium like air or water, and its frequency determines how we perceive it. Human ears can detect sounds in the range of 20 Hz to 20,000 Hz, which is known as the audible range.  

![](assets/photo_5332330176228484737_y.jpg)  

Ultrasonic sound refers to sound waves with frequencies above 20,000 Hz—too high for human hearing. Despite being inaudible to us, these high-frequency sound waves are extremely useful in various applications. The unique properties of ultrasonic sound, such as its ability to reflect off objects and maintain its directionality, make it ideal for measuring distances, detecting objects, and even medical imaging (like ultrasounds).       

### What is the Piezoelectric Effect?    

The piezoelectric effect is the property of certain materials (quartz, ceramics like PZT(lead zirconate titanate)) to generate an electric signal in response to applied mechanical stress. The reverse is also true: applying an electric field to these materials causes them to deform or vibrate mechanically.  
 
**Direct Piezoelectric Effect**  

When you apply pressure or strain to a piezoelectric material, its internal structure generates an electrical charge. This property is useful for creating sensors that convert mechanical energy (like vibrations) into electrical signals.

**Reverse Piezoelectric Effect**

When you apply an electrical voltage to a piezoelectric material, it changes shape or vibrates. This is useful for creating actuators or devices that produce sound waves, such as ultrasonic transmitters. 

### What is a transducer?     

A transducer is a device that converts one form of energy into another. It is commonly used in measurement, sensing, and control systems. Transducers play a critical role in many engineering and scientific applications, as they bridge the gap between physical phenomena and electronic signals that can be measured or controlled. In the context of HC-SR04 ultrasonic sensor, it is basically piezoelectric transducer, device that uses the piezoelectric effect to convert between mechanical energy (such as vibrations or pressure) and electrical energy.   

![](assets/photo_5332330176228484712_y.jpg)  

The provided image shows a diagram of a piezoelectric transducer, which is a device that converts electrical energy into mechanical vibrations (sound) or vice versa, using the piezoelectric effect.  
 
Components  

**Metal Outer Casing** 
 The metal outer casing provides structural support and protection for the internal components of the transducer. It also helps to shield the piezoelectric element from external mechanical impacts and electrical noise. 
  
**Crystal Piezo Element** 
 The core of the transducer, this piezoelectric crystal, generates mechanical vibrations when an electrical voltage is applied (or generates an electrical signal when it experiences mechanical stress). Common materials used include quartz, lead zirconate titanate (PZT), and other ceramics. 
  
**Piezoelectric Effect**
 This is the property of certain materials to generate an electric charge in response to applied mechanical stress. Conversely, they can deform (change shape) when an electric field is applied. 
  
**Electrodes** 
 These are conductive layers placed on either side of the piezoelectric element to apply an electrical voltage across it or to collect the electrical charge generated by it. The electrodes enable the piezoelectric effect to be utilized in a controlled manner.  Electrodes are typically made of thin metal films and are in direct contact with the piezoelectric element to ensure efficient transfer of electrical energy. 
  
**Diaphragm Membrane**
 The diaphragm membrane is a flexible component that vibrates in response to the mechanical movement generated by the piezoelectric element. This vibration is what produces sound waves in ultrasonic transducers or captures sound waves in microphones. The diaphragm is crucial in converting the mechanical vibrations of the piezoelectric element into sound waves (or vice versa). It needs to have the right balance of flexibility and strength to effectively transmit these vibrations. 
  
**Working Principle**  

*Transmission Mode (Generating Sound)*  
Electrical to Mechanical: When an alternating voltage is applied across the electrodes, the piezoelectric element deforms and vibrates. These vibrations are transmitted to the diaphragm, which in turn generates sound waves (ultrasonic waves) that propagate through the medium (air, water, etc.). 
  
*Reception Mode (Detecting Sound):*  
Mechanical to Electrical: When sound waves hit the diaphragm, they cause it to vibrate. These vibrations are transferred to the piezoelectric element, which deforms and generates an electrical signal across the electrodes. This signal can then be processed and measured.


   






