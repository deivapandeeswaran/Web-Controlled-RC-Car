# Web-Controlled-RC-Car
This project involves building a web-controlled RC car using a Raspberry Pi 4. The car can be controlled via a web interface, which allows for forward and backward motion, steering control, and live video streaming. The project is designed to provide a practical and fun way to explore robotics, embedded systems, and web development.
## Table of Contents
1. [Introduction](#Introduction)
2. [Materials_and_Components](#Materials_and_Components)
3. [System_Architecture](#System_Architecture)
4. [Software_Installation](#Software_Installation)
5. [Hardware_Setup](#Hardware_Setup)
6. [Usage](#Usage)
7. [Project_Details](#Project_Details)
8. [Future_Improvements](#Future_Improvements)
9. [Contributing](#Contributing)

## Introduction
The Web-Controlled RC Car project integrates hardware and software components to create a remotely controllable car. The car is powered by a Raspberry Pi 4, which interfaces with motors, LEDs, and a webcam. The control interface is built using Flask and OpenCV, allowing for real-time video streaming and responsive controls.

## Materials and Components
### Hardware
1. **Raspberry Pi 4 :** The main controller for the car.
2. **LiPo Battery and DC-DC Converter :** Provides a stable power supply to the Raspberry Pi and motors.
3. **Motors and Motor Driver :** Drives the car forward, backward, and controls steering.
4. **Microsoft HD Webcam :** Captures live video for streaming.
5. **Breadboard and Connecting Wires:** Facilitates connections between components.
6. **LEDs for Headlights :** Provides illumination controlled by the Raspberry Pi.
### Software
1. **Raspberry Pi OS (Ubuntu 22.04 LTS Server)**
2. **Python 3**
3. **Flask**
4. **RPi.GPIO**
5. **OpenCV**
6. **HTML/CSS/JavaScript**
## System Architecture
### GPIO Control
The RPi.GPIO library is used to control the GPIO pins on the Raspberry Pi. The GPIO pins are configured for output to control the motors and LEDs. The motor driver receives signals to control the forward and backward motion of the car, as well as the steering mechanism.

### PWM for Steering
PWM (Pulse Width Modulation) signals are used to control the steering motor, allowing for smooth and precise adjustments to the wheel angle. The RPi.GPIO library facilitates the generation of PWM signals.

### Video Streaming
The video feed from the webcam is integrated into the Flask application using OpenCV. Frames are captured and streamed to the web interface in real-time, providing live video feedback to the user.
