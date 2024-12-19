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

Light is a form of electromagnetic radiation that exhibits wave-particle duality, meaning it can behave both as a wave and as a particle (photon). It is characterized primarily by its wavelength and frequency. The electromagnetic spectrum is divided into different segments or bands, including radio waves, microwaves, infrared, visible light, ultraviolet, X-rays, and gamma rays.   

![](assets/infrared-waves-definition-uses-examples_01001114_133518.jpg)  

*Visible light*, also known as white light, ranges in wavelength from 0.4 to 0.8 micrometers (µm). It is mainly emitted by the sun and can be reflected, absorbed, or transmitted by objects. When white light strikes an object, some wavelengths are absorbed, while others are reflected. The reflected wavelengths determine the color we perceive.  

![](assets/Screenshot 2024-12-17 115237.png)  

*Infrared light* has wavelengths ranging from 0.8 to 50 micrometers (µm), making it invisible to the human eye. Some animals, such as snakes, can detect infrared radiation, which corresponds to the thermal energy emitted by objects. Any object with a temperature above absolute zero (0 Kelvin or -273°C) emits infrared radiation, both during the day and at night.  

### Infrared Radiation and Temperature  

When objects heat up, their radiation changes in two significant ways:  

*Increased Emission Across All Wavelengths*  
 As an object becomes hotter, the object emits more radiation across all wavelengths. This makes the object appear brighter overall.    

*Shift in Peak Emission*  
The second thing that happens is that the peak of the emission shifts from the red all the way up through the blue. It goes on even further, the peak emission can shift beyond visible light into the ultraviolet region.  


### Wien's Displacement Law  
Wien's Displacement Law describes the relationship between the temperature of a black body and the wavelength at which it emits the most radiation. This law is essential for understanding the thermal emission of objects. Wien's Displacement Law is expressed as:  

![](assets/Screenshot 2024-12-18 200054.png)  
                                                                      
Where:  
**λmax** is the wavelength of maximum emission (in meters).  
**𝑇** is the absolute temperature of the black body (in Kelvin, K).  
**𝑏** is Wien's constant, approximately 2.897×10^−3 mK.   

**Note**  
*λmax* is the wavelength where the intensity of radiation is the highest, but the object still emits radiation at other wavelengths.  

As the temperature of an object increases, the wavelength at which it emits the most energy decreases (i.e., shifts toward shorter wavelengths like visible or ultraviolet light). Conversely, cooler objects emit most of their radiation at longer wavelengths (infrared or microwave regions).  

![](assets/Screenshot 2024-12-17 182540.png)

### Bonus Information: Explanation of Why sunlight is white?  
The Sun's surface temperature is about 5800 Kelvin (K). By using Wien's constant, the peak wavelength of sunlight from formula is approximately 502 nm. This corresponds to green light in the visible spectrum. So from Physics perspective, the Sun must appear green right? Before questioning Physics, let me finish my explanation.  

**Why the Sun Doesn't Appear Green**  
This is more to do with Biology than Physics. Even though the Sun’s radiation peaks in the green region, it emits a broad spectrum of light that includes significant amounts of red, blue, and other colors. Our eyes have three types of cone cells sensitive to red, green, and blue light. Our eyes have not evolved to distinguish colour of highest intensity from colours of lower intensity, therefore the brain interprets the combination of all these wavelengths as white light.  

![](assets/Screenshot 2024-12-18 200803.png)  

The physics of blackbody radiation and Wien's Law are accurate, but the perception of color is influenced by biology (human vision) and how our brain processes light from the entire spectrum.  

The higher the temperature of a body, the closer its emitted radiation is to the visible light spectrum. Also, when a blacksmith heats a piece of iron until it is "white-hot," it emits radiation across all visible wavelengths, making it appear white.  

![](assets/Screenshot 2024-12-17 120043.png)  


### Rayleigh-Jeans law  
The Rayleigh-Jeans Law is a formula that describes the spectral radiance of electromagnetic radiation emitted by a blackbody at a given temperature T. It is an approximation that applies at long wavelengths (or low frequencies) and is derived based on classical physics.  

![](assets/image.png)  

Where:  
Bλ(T) is the spectral radiance (power emitted per unit area per unit wavelength).  
c is the speed of light (≈ 3 × 10^8 m/s).  
kB is Boltzmann's constant (≈ 1.38 × 10^−23 J/K).  
T is the absolute temperature of the blackbody in Kelvin.  
λ is the wavelength.  

The Rayleigh-Jeans Law accurately predicts the behavior of blackbody radiation at long wavelengths (low frequencies). When it comes to short wavelengths (high frequencies), the law predicts an infinite amount of energy, which contradicts experimental results. This discrepancy, known as the "ultraviolet catastrophe," was one of the critical failures of classical physics and led to the development of quantum mechanics.  


### Ultraviolet Catastrophe  
The ultraviolet catastrophe refers to a major problem in classical physics when predicting the radiation emitted by a blackbody at different wavelengths. This issue was particularly evident in the 19th century, and its resolution led to significant advancements in the field of quantum physics. The problem with the Rayleigh-Jeans Law was resolved by Max Planck, who introduced Planck's Law of blackbody radiation in 1900. Planck's Law accurately describes the spectral radiance across all wavelengths.  

![](assets/61QqQ.gif)  

**What Was the Problem?**  
Classical physics, particularly the Rayleigh-Jeans law, treated energy as continuous. According to classical theory, a blackbody could emit radiation at any frequency, and the energy emitted at a given frequency was not restricted. This led to the prediction that as the wavelength of radiation decreases (moving towards the ultraviolet region), the intensity would increase without bound—this is the ultraviolet catastrophe.  

From Rayleigh-Jeans Law, as λ approaches 0 (shorter wavelengths), the intensity approaches infinity, which clearly contradicted experiments.      

**Solution by Planck**  
Planck realized that this continuous energy assumption was not correct. He proposed that energy was not emitted continuously, but rather in discrete packets, which he called quanta. Each quantum of energy was proportional to the frequency of the radiation:  

![](assets/0_xN008-8vedYoNJAs.jpg)  

This assumption led to the idea that energy levels in a system could only take certain discrete values, rather than any value.  


### Planck's Law  

Using the concept of quantized energy, Planck derived a new formula for the spectral radiance of blackbody radiation, which replaced the Rayleigh-Jeans law. Planck's Law describes the spectral distribution of electromagnetic radiation emitted by a black body at a given temperature. It provides a formula for calculating the spectral radiance, or the intensity of electromagnetic radiation at a specific wavelength and temperature. This law resolved the “ultraviolet catastrophe” predicted by classical physics, laying the foundation for quantum mechanics.  

![](assets/Screenshot 2024-12-17 201747.png)  

B(λ, T) = Spectral radiance (W·sr⁻¹·m⁻³)  
h = Planck's constant (6.626 × 10^−34 J·s)  
c = Speed of light (3.00 × 10^8 m/s)  
λ = Wavelength of radiation (m)  
kB = Boltzmann's constant (1.381 × 10^−23 J/K)  
T = Absolute temperature (K)  

From Planck's Law, we can see that:  

*Wavelength Dependence*  
 The amount of radiation emitted depends on the wavelength (λ).  

*Temperature Influence*  
As the temperature (T) increases, the peak of the emission curve shifts to shorter wavelengths (described by Wien's Displacement Law).  

*Quantum Nature*
The exponential term reflects the quantized nature of radiation, which was a breakthrough in explaining how energy is emitted in discrete packets (quanta).  

*At high frequencies (short wavelengths),* the exponential factor dominates, which causes the intensity to decrease exponentially. This prevented the intensity from diverging, as classical theory had predicted. Instead of the radiation intensity growing infinitely at small wavelengths (the ultraviolet catastrophe), Planck's formula predicted a smooth decrease in intensity.  
*At low frequencies (long wavelengths)*, Planck's law approximates the Rayleigh-Jeans law, meaning it agrees with classical predictions for lower energy levels (where the temperature is not very high). This matched experimental data well for longer wavelengths.

Infrared cameras and thermal imaging devices rely on Planck's law to measure temperature.  


### Stefan-Boltzmann's Law  
Stefan-Boltzmann's Law describes the power radiated by a black body in terms of its temperature. It states that the total energy emitted per unit surface area of a black body is proportional to the fourth power of its absolute temperature.  

![](assets/336003550.gif)  
                                                                
Where:  
P = Power radiated per unit surface area (W/m²).  
σ = Stefan-Boltzmann constant = 5.67 × 10^−8 W/m2K4.  
T = Absolute temperature in Kelvin (K).  

For real materials (which are not perfect black bodies), we also multiply with emissivity of the material.   

ϵ = Emissivity of the material (0 ≤ ϵ ≤ 1).  
A perfect black body has an emissivity 𝜖 = 1, while a perfect reflector has 𝜖 = 0.  

Higher temperatures lead to exponentially higher radiation due to the T^4 relationship. As an object's temperature increases, it radiates more energy, and this radiation spans a range of wavelengths, including visible light. At higher temperatures, a greater proportion of the emitted radiation falls within the visible spectrum (Wien's Displacement Law). This is why:  

Hotter objects (like stars) appear brighter and often shift towards bluish-white colors.  
Cooler objects emit less radiation and may glow red or not emit visible light at all.  

                                            
### Kirchhoff's Law of Thermal Radiation  
The law states that for any object at thermal equilibrium (balance), the emissivity of a surface is equal to its absorptivity. In simple terms,  
**"A good absorber is also a good emitter at the same wavelength and temperature."**  

*Emissivity (ε):* As l explained, the fraction of radiation emitted by the surface compared to a perfect black body at the same temperature.  
*Absorptivity (α):* The fraction of incident radiation absorbed by the surface.  
At thermal equilibrium:
                                                                    **𝜀 = 𝛼**  

Perfect black body: Has an emissivity and absorptivity of 1 (ε = α = 1).  
Reflective surfaces: Poor absorbers, so they are also poor emitters.  A dark surface absorbs more radiation (high absorptivity) and thus emits more radiation at the same temperature. (Black Body in this context).

### The Concept of a Black Body

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

*Planck's Law:* Describes the spectral distribution of radiation emitted by a black body at a given temperature.  
*Wien's Displacement Law:* States that the wavelength at which a black body emits the most radiation shifts as its temperature changes. Higher temperatures shift the peak emission toward shorter wavelengths (e.g., visible light).  
Stefan-Boltzmann Law: Indicates that the total power radiated by a black body is proportional to the fourth power of its temperature.  

### Bonus Information: Why are objects with emissivity near that of a black body more luminous?  

When emissivity ϵ ≈ 1, it means the object is efficient emitter of radiation, this can be explained through Stefan-Boltzmann's Law and the concept of emissivity. If an object has an emissivity near 1 (like a black body), it radiates more power compared to objects with lower emissivity at the same temperature. For instance, stars are excellent approximations of black bodies because they absorb and emit radiation extremely efficiently across a wide spectrum of wavelengths. Their high temperature (ranging from thousands to millions of Kelvin) means they radiate a huge amount of power according to Stefan-Boltzmann's Law. Their emissivity is very close to 1 because they don't reflect much radiation — almost all the energy is emitted as light and other forms of radiation. Higher temperature results in exponentially higher radiation (T - P relationship). This combination of high temperature and high emissivity makes objects like stars incredibly luminous (they emit vast amounts of light).




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








  


