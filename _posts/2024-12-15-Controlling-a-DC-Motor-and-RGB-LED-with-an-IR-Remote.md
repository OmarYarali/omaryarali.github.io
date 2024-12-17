---
title: Controlling a DC Motor and RGB LED with an IR Remote
date: 2024-12-15 00:00:00 +0300
categories: [IoT, Arduino]
tags: [Embedded Project, Electronics, IR, NEC, Remote, RGB LED, DC Motor, Control, Integrated Circuit, Motor Driver, Power Supply]   
author: yarali 
published: true

---  

## Introduction  

This project focuses on using an IR remote to control both a DC motor and an RGB LED, showcasing how versatile and practical IR technology can be. The DC motor is equipped with functionality for adjusting its speed and direction, allowing for precise control over its operation. Simultaneously, the RGB LED can display six distinct colors, along with an off state, and its brightness can be fine-tuned to match desired intensity levels.

Additionally, I explore how the DC motor's functionality—such as adjusting its speed and reversing its direction—can be seamlessly managed using the same IR remote. This project serves as a great example of combining creativity with technology to build a versatile and interactive system for various applications.

Whether you're a hobbyist or an aspiring electronics enthusiast, this project provides insights into the practical use of IR technology for remote-controlled operations. 

## Overview  

The setup includes integrating the IR receiver module with an Arduino, allowing it to decode the signals sent by the remote. By mapping specific remote buttons to each function, the system enables intuitive control over the motor and LED. This combination of hardware and software demonstrates an efficient and interactive way to build remote-controlled systems that can be adapted to a variety of creative and practical applications.

## Features of Project  

**DC Motor Speed Control**  
The IR remote allows precise control over the speed of the DC motor. By pressing specific buttons, you can increase or decrease the motor's speed, making it ideal for applications where variable motor speed is required, such as robotics or conveyor systems.  

**DC Motor Direction Control**  
The motor's direction can be toggled between clockwise and counterclockwise using the IR remote. This feature is crucial for systems that require bidirectional movement, like robotic arms or automated gates.  

**Dc Motor On/Off Control**  
The IR remote provides an easy way to turn the DC motor on and off with a dedicated button. This feature ensures efficient power management and allows you to quickly stop the motor when it’s not in use. By pressing the assigned button, you can toggle the motor's state between active and inactive, making it convenient for applications that require intermittent motor operation.  

**RGB LED Color Control**  
The RGB LED can display six distinct colors (Red, Green, Blue, Cyan, Magenta, Yellow), allowing for vibrant visual feedback. Each color is activated by a designated button on the IR remote, making it easy to switch between colors.  

**RGB LED Intensity Adjustment**  
The brightness of the RGB LED can be adjusted using the IR remote. This feature lets you dim or brighten the LED as needed, which can be useful for mood lighting, notifications, or energy-saving purposes.  

**LED On/Off Control**  
The IR remote includes a dedicated button to turn the RGB LED off completely. This is a convenient feature for conserving power or when the LED is not required.  

**Seamless IR Remote Integration**  
The project uses an IR receiver module to decode signals from the remote. Each button is programmed to correspond to a specific function, ensuring a user-friendly and responsive control system.  

**Interactive and Versatile Design**  
By combining control over both a motor and an LED, this project demonstrates the versatility of IR technology and showcases how a single remote can manage multiple components efficiently. 

## Required Components  

Arduino Nano (for better portability)  
IR Remote  
IR Receiver Module  
DC Motor  
Motor Driver Module (L298N or L293D)  
RGB LED
Resistors (3 piece 220Ω or 330Ω)  
Breadboard and Jumper Wires  
External Power Supply  (For Motor)  
Download IRremote Library (4.4.1)  

## How to Download Libraries  

If you’re not familiar with downloading and installing libraries in the Arduino IDE, you can check out my  [Portable Humidity and Temperature Sensor](https://omaryarali.github.io/posts/Portable-Humidity-and-Temperature-Sensor/) for a comprehensive explanation.  
```c
#include <IRremote.hpp>
```  


## What is Infrared Light?  

### What is Light?  

Photos are taken from Teledyne FLIR and  LYNRED.  

Light is an electromagnetic wave characterized primarily by its wavelength. The light spectrum is divided into segments or spectral bands.  

![](assets/infrared-waves-definition-uses-examples_01001114_133518.jpg)  

*Visible light*, also known as white light, ranges in wavelength from 0.4 to 0.8 micrometers (µm). It is mainly emitted by the sun and can be reflected, absorbed, or transmitted by objects. When white light strikes an object, some wavelengths are absorbed, while others are reflected. The reflected wavelengths determine the color we perceive.  

![](assets/Screenshot 2024-12-17 115237.png)  

*Infrared light* has wavelengths ranging from 0.8 to 50 micrometers (µm), making it invisible to the human eye. Some animals, such as snakes, can detect infrared radiation, which corresponds to the thermal energy emitted by objects. Any object with a temperature above absolute zero (0 Kelvin or -273°C) emits infrared radiation, both during the day and at night.  

### Infrared Radiation and Temperature  

**Wien's Displacement Law**  
Wien's Displacement Law describes the relationship between the temperature of a black body and the wavelength at which it emits the most radiation. This law is essential for understanding the thermal emission of objects. Wien's Displacement Law is expressed as:  
 **𝜆max = 𝑏/𝑇**, where  

λmax is the wavelength of maximum emission (in meters).  
𝑇 is the absolute temperature of the black body (in Kelvin, K).  
𝑏 is Wien's constant, approximately 2.897×10^−3 mK.   

As the temperature of an object increases, the wavelength at which it emits the most energy decreases (i.e., shifts toward shorter wavelengths like visible or ultraviolet light). Conversely, cooler objects emit most of their radiation at longer wavelengths (infrared or microwave regions).  

![](assets/Screenshot 2024-12-17 182540.png)

### Bonus Information: Explanation of Why sunlight is white?  

The Sun's surface temperature is about 5800 Kelvin (K). By using Wien's constant, the peak wavelength of sunlight from formula is approximately 502 nm. This corresponds to green light in the visible spectrum. So from Physics perspective, the Sun must appear green right? Before questioning Physics, let me finish my explanation.  

**Why the Sun Doesn't Appear Green**  
This is more to do with Biology than Physics. Even though the Sun’s radiation peaks in the green region, it emits a broad spectrum of light that includes significant amounts of red, blue, and other colors. Our eyes have three types of cone cells sensitive to red, green, and blue light. Our eyes have not evolved to distinguish colour of highest intensity from colours of lower intensity, therefore the brain interprets the combination of all these wavelengths as white light.  


![](assets/image.png)  

The physics of blackbody radiation and Wien's Law are accurate, but the perception of color is influenced by biology (human vision) and how our brain processes light from the entire spectrum.  

The higher the temperature of a body, the closer its emitted radiation is to the visible light spectrum. Also, when a blacksmith heats a piece of iron until it is "white-hot," it emits radiation across all visible wavelengths, making it appear white.  

![](assets/Screenshot 2024-12-17 120043.png)  

### Planck's Law  

This relationship between temperature and emitted radiation is described by Planck's Law, which calculates the intensity of thermal radiation (or radiance) for a given temperature. Planck's Law describes the spectral distribution of electromagnetic radiation emitted by a black body at a given temperature.  

![](assets/Screenshot 2024-12-17 115423.png)  

Lλ = Spectral radiance (W·sr⁻¹·m⁻³)  
h = Planck's constant (6.626 × 10^−34 J·s)  
c = Speed of light (3.00 × 10^8 m/s)  
λ = Wavelength of radiation (m)  
kB = Boltzmann's constant (1.381 × 10^−23 J/K)  
T = Absolute temperature (K)  

#### The Concept of a Black Body

**Black Bodies and Emissivity**  
A black body is a theoretical object that absorbs all incident wavelengths and emits radiation solely based on its temperature. The efficiency with which real objects emit radiation is expressed by their emissivity, a value ranging from 0 to 1. Emissivity compares the radiance of a body to that of a black body.  

An emissivity of 1 means the body emits radiation as efficiently as a black body.
An emissivity of 0.5 means the body emits half the radiation of a black body.  

*Emissivity* depends on an object's physical properties. For example:  
Human skin has a high emissivity of around 0.98.  
Polished metals, like aluminum, can have emissivity values below 0.1, making them effective infrared reflectors (infrared mirrors).   
Knowing an object's emissivity allows for the accurate calibration of infrared devices, enabling precise temperature measurement.  

**How a Black Body Works**  
*Absorption*  
A black body absorbs all electromagnetic radiation that strikes it, regardless of wavelength. This means it does not reflect or transmit any light—hence the term "black body".  

*Emission*  
According to its temperature, a black body emits thermal radiation across a range of wavelengths. This emission follows Planck's Law, which describes how the intensity and distribution of emitted radiation depend on temperature.  

*Thermal Radiation*  
Thermal radiation is the electromagnetic radiation emitted by any object with a temperature above absolute zero (0 Kelvin or -273.15°C). A black body emits the maximum possible radiation at every wavelength for its temperature.  






### Discovery of Infrared Radiation  

Up until 1800, visible light was the only known part of the electromagnetic spectrum that's when astronomer Sir William Herschel discovered a whole new world of infrared radiation. This discovery marked a significant milestone in understanding the electromagnetic spectrum beyond visible light.  

**Using a Prism to Split Sunlight**
Herschel passed sunlight through a glass prism, which split the white light into its constituent colors (a spectrum of red, orange, yellow, green, blue, indigo, and violet). In his observations of sunlight, Herschel experimented with colors of light and noticed each one passed a different amount of heat.  

**Measuring Heat in Different Colors**  
To measure the heat associated with each color of light, he used thermometers with blackened bulbs. The blackened bulbs helped absorb more heat for accurate temperature readings.  

![](assets/IR Experiment.png)  

**Observation of Red Light**  
Herschel noted that the temperature increased as he moved the thermometer from blue to red. The temperature reading was highest in the red part of the spectrum.  

**Beyond Red Light**  
Out of curiosity, Herschel extended his thermometer just beyond the red part of the spectrum where no visible light was present. To his surprise, the thermometer showed a temperature even higher than in the visible red light region.  

Herschel concluded that there must be an invisible form of radiation beyond red light, which was responsible for the increased heat. He named this new discovery *“infrared radiation”*, from the Latin words:  

“Infra” = below  
“Red” = refers to its position below red in the visible spectrum.  

This experiment revealed that the electromagnetic spectrum extends beyond visible light, laying the foundation for understanding other types of electromagnetic waves such as ultraviolet (UV), X-rays, and radio waves. This breakthrough paved the way for future discoveries in the electromagnetic spectrum, leading to innovations in communication, astronomy, and medicine. Infrared radiation is now used in various fields like night vision, thermal imaging, remote sensing, and medical diagnostics.   








  


