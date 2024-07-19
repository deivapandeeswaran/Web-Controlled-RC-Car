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

## Software Installation
1. **Clone the Repository**
```bash
git clone https://github.com/yourusername/web-controlled-rc-car.git
cd web-controlled-rc-car
```
2. **Install Dependencies**
```bash
sudo apt-get update
sudo apt-get install python3-pip
pip3 install flask opencv-python RPi.GPIO
```

## Hardware Setup
1. **Connect the Motors and Motor Driver**
* Connect the motor driver to GPIO pins on the Raspberry Pi.
* Connect the motors to the motor driver.

2. **Connect the Webcam**
* Connect the webcam to a USB port on the Raspberry Pi.

3. **Power the Raspberry Pi**
* Connect the LiPo battery to the DC-DC converter.
* Set the DC-DC converter to output 5V.
* Connect the output to the 5V and GND pins on the Raspberry Pi.
## Usage
1. **Start the Flask Application**
```bash
python3 app.py
```

2. **Access the Web Interface**
Open a web browser on your mobile device or computer.
Navigate to 'http://<raspberry_pi_ip_address>:5000'

3. **Control the Car**
Use the web interface to control the car's forward, backward, and steering movements.
View the live video stream from the webcam.

# Project Details
## GPIO Setup
The GPIO pins are configured in the app.py file:
```bash
# GPIO setup
GPIO.setmode(GPIO.BCM)
GPIO.setup(17, GPIO.OUT)  # Steering
GPIO.setup(27, GPIO.OUT)
GPIO.setup(22, GPIO.OUT)  # Motor
GPIO.setup(23, GPIO.OUT)
GPIO.setup(24, GPIO.OUT)  # Headlight
```

## PWM for Steering
PWM signals are generated to control the steering motor:
```bash
pwm = GPIO.PWM(17, 100)
pwm.start(0)
```
## Video Streaming
The video feed is captured and streamed using OpenCV:
```bash
def gen_frames():
    while True:
        success, frame = camera.read()
        if not success:
            break
        else:
            ret, buffer = cv2.imencode('.jpg', frame)
            frame = buffer.tobytes()
            yield (b'--frame\r\n'
                   b'Content-Type: image/jpeg\r\n\r\n' + frame + b'\r\n')
```
## Future Improvements
* Add Autonomous Navigation: Implement obstacle detection and autonomous navigation.
* Enhance Web Interface: Improve the user interface with more controls and features.
* Battery Management: Add battery monitoring and management for better safety and performance.


