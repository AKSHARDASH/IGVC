# Team Anvrit - IGVC AutoNav Participation

Welcome to the repository for Team Anvrit's contribution to the IGVC AutoNav competition, hosted by Oakland University. This repository contains the schematic and board files for the custom PCB used in our vehicle.

![image](https://github.com/AKSHARDASH/IGVC/assets/134735494/aaa28f90-7877-4497-8308-ecb855bbfb37)


![image](https://github.com/AKSHARDASH/IGVC/assets/134735494/31d962fd-73ca-4f5c-8ccb-de330cdd8d4f)

## Overview

Our PCB design incorporates several unique features essential for tackling the problem statements of the IGVC AutoNav. The key functionalities of the PCB include:

- **Radio Kill Switch**: Utilizes a 433 MHz wireless receiver fixed on the PCB for remote vehicle shutdown.
- **Low Battery Kill Switch**: Implemented using a TL431 IC to ensure safe operation by shutting down the system when the battery voltage drops below a threshold.
- **Sensor Data Handling**: An Arduino Nano collects data from various sensors such as GPS, IMU, and wheel encoders, and transmits the data to the controlling computer using serial communication.

## PCB Features

### Radio Kill Switch
![image](https://github.com/AKSHARDASH/IGVC/assets/134735494/2cb3a57f-9df4-444b-89d5-1742bc182874)

The radio receiver is active low. A simple yet efficient method to kill the vehicle wirelessly is devised using an AND gate IC. The two inputs of the AND gate are the required PWM signal and the radio data. When data is received, the data pin goes low, resulting in the output of the AND gate (connected to the motor driver) being 0, effectively stopping the vehicle.

### Low Battery Kill Switch
![image](https://github.com/AKSHARDASH/IGVC/assets/134735494/7f9a73df-633e-4e81-9ced-232d77955392)

A TL431 IC is used to monitor the battery voltage. The reference terminal of the TL431 is kept above 2.5V using a simple voltage divider network. When the battery voltage falls below a certain threshold, the TL431 stops driving the PMOS connected to it, shutting down the entire system to prevent damage.


## System Architecture

1. **Sensor Data Collection**: An Arduino Nano gathers data from the GPS, IMU, and wheel encoders.
2. **Data Transmission**: The Arduino Nano sends the collected sensor data to the controlling computer via serial communication.
3. **ROS Integration**: The computer runs a ROS script that reads the data and publishes it to a ROS topic for further processing.
4. **Motor Control**: The computer calculates the desired RPM and sends this information back to the Arduino Nano. The Arduino then controls the motors by adjusting the PWM values accordingly.

## Repository Contents

- **Schematics**: The schematic files for the PCB design.
- **Board Files**: The board layout files for the PCB.

## Getting Started

To get started with using the PCB and running the vehicle, follow these steps:

1. **Clone the Repository**: Clone this repository to your local machine using `git clone`.
2. **Upload Arduino Code**: Upload the Arduino code to the Arduino Nano.
3. **Run ROS Script**: Set up and run the ROS script on the controlling computer to handle the sensor data and motor control.


![WhatsApp Image 2024-06-30 at 01 53 59_3bbd68f7](https://github.com/AKSHARDASH/IGVC/assets/134735494/a9d21331-cba7-47e2-9be6-ae4ddba22757)


