---
title: ECE 196 Team 1 - Tutorial: Anti-Theft Unit for Electric Scooters

date: 2024-11-18
authors:
  - name: Yijie He
  - name: Junyi Wu
---

![relevant graphic or workshop logo](image/path)

## Introduction

This tutorial guides you through building a custom anti-theft security system for electric scooters. With the alarming rate of increasing micro-mobility device theft such as electric scooters and bicycles on campus, it is very important to secure your electric scooter. Both of our team members have experienced their electric scooters being stolen in the past, and we know how important the issue is, so we want to help any UCSD student who is concerned by this issue. Our solution provides an affordable and effective way to secure your electric scooter using readily available components. We hope this tutorial can help you secure your electric scooter, gaining some practical embedded development skills, and save you from the headache of dealing with stolen scooters.

### Learning Objectives

- Understanding basic electronics and microcontroller programming
- Understanding basic PCB design
- Building a motion detection system with BNO sensors
- Developing practical problem solving skills

### Background Information

Micro-mobility devices, including bikes and electric scooters, are easily stolen on the UCSD campus. 
According to the 2024 Annual Security & Fire Safety Report from the UCSD Police Department, theft of micro-mobility devices such as electric scooters and bicycles has increased at an alarming rate. Causing thousands of dollar lost and extremely inconvenience for students and faculties.
![relevant graphic or workshop logo](./stats_20about_20theft.jpg)

## Getting Started

For any software prerequisites, write a simple excerpt on each
technology the participant will be expecting to download and install.
Aim to demystify the technologies being used and explain any design
decisions that were taken. Walk through the installation processes
in detail. Be aware of any operating system differences.
For hardware prerequisites, list all the necessary components that
the participant will receive. A table showing component names and
quantities should suffice. Link any reference sheets or guides that
the participant may need.
The following are stylistic examples of possible prerequisites,
customize these for each workshop.

### Required Downloads and Installations

List any required downloads and installations here.
Make sure to include tutorials on how to install them.
You can either make your own tutorials or include a link to them.

### Required Components

This is all the electrical components needed for the project.

| Component Name | Quantity |
|----------------|-----------|
| ESP32-S3 Dev Board | 1 |
| ESP32-C6-MINI-1-N4 | 1 |
| JS102011SAQN Slide Switch | 5 |
| Conn_01x05 PinHeader_1x05_P2.54mm_Vertical | 1 |
| 603 0.1uF Capacitor | 4 |
| 603 10kΩ Resistor | 3 |
| 603 2.2kΩ Resistor | 4 |
| BNO085 Sensor | 2 |
| 3W DC Speaker | 1 |
| LP103454 3.7V Battery | 2 |
| Dupont Wire | Based On Need |

You also need to 3D-printed some enclosures for putting the boards onto your scooter and your lock.

### Required Tools and Equipment
Soldering station, hot plate, solder paste, bike lock, e-scooter/bike.  
Not required, but recommended: logic analyzer, stencil holder.

## Part 01: ESP32

### Introduction

In this section we are about to introduce how to use platform IO to build firmware.

### Objective

- List the learning objectives of this section

### Background Information

Give a brief explanation of the technical skills learned/needed
in this challenge. There is no need to go into detail as a
separation document should be prepared to explain more in depth
about the technical skills

### Components

- List the components needed in this challenge

### Instructional

Teach the contents of this section

## Part 02: BNO 085

### Introduction

This section is about how to use and BNO 085 IMU on ESP32

### Objective

- learn critical thing about BNO wiring using I2C.  
- Software on how to get BNO data.  

### Background Information

Give a brief explanation of the technical skills learned/needed
in this challenge. There is no need to go into detail as a
separation document should be prepared to explain more in depth
about the technical skills
To do this part, you will need:  
- Know how to use Kicad/Altium.
- know how to do SMT soldering.

### Components

- Computer with Kicad 8.0+

### Instructional

1. On BNOs you would need to configure the communication protocals, and if you are using an internal clock or external crystal. In this instruction, we would use I2C and internal clock.
2. First we would need to configure I2c
   the following are pins configuration:
- The H_INTN pin is the application interrupt line that indicates the BNO08X requires attention. This should be
tied to a GPIO with wake capability. The interrupt is active low.
- NRST is the reset line for the BNO08X and can be either driven by the application processor or the board reset.
- BOOTN is sampled at reset. If low the BNO08X will enter bootloader mode.
- Pin 4 (BOOTN) should be pulled high through a 10K Ohms resistor. To use the device firmware update (DFU)
capability of the BNO08X, it is recommended to connect Pin 4 to a GPIO pin on the external microcontroller.
-  Pin 5 (PS1) and Pin 6 (PS0/WAKE) are the host interface protocol selection pins. These pins should be tied to ground to select the I2C interface.
-  Pin 17 (SA0) can be used to select the lower bit of the 7-bit I2C slave device address, BNO's I2C address can be 4A or 4B, 4B is for slave device. Ground this pin will set BNO as master, connect to 3.3v will make this BNO In slave mode.
- Pull up resistors (R1 and R2) are needed on the I2C communication lines - Pin 19 (HOST_SCL) and Pin 20 (HOST_SDA). These values may vary depending on the board design and bus capacitance, but typical
values are between 2KΩ and 4KΩ.
- The BNO08X supports environmental sensors (e.g. pressure sensors, ambient light sensors) on a secondary I2C interface. This interface should be pulled up via resistors regardless of the presence of the external sensor as the SW polls for sensors at reset. In another world, BNO can also work as a master device.
3. Then we need to configure the correct clock mode:
  To do that we need to pull up pin 10(CLKSEL0), and pull down pin 26(CLKSEL1). If you want to usd external crystal, please refer to BNO datasheet page 11.


## Example

### Introduction

Introduce the example that you are showing here.

### Example

Present the example here. Include visuals to help better understanding

### Analysis

Explain how the example used your tutorial topic. Give in-depth analysis of each part and show your understanding of the tutorial topic

## Additional Resources

### Useful links

List any sources you used, documentation, helpful examples, similar projects etc.
