# ESP-Based Wireless Security Camera System

## Project Overview

This project focuses on the development of a compact, low-power wireless security camera system using an ESP microcontroller and a Raspberry Pi processing cluster.

The system uses an ESP-based camera node to capture and transmit video to a central Raspberry Pi cluster for computer vision processing, recording, and monitoring.

To minimise power consumption, the camera node incorporates a custom PIR motion detection circuit designed around analogue signal conditioning and low-power interrupt-based operation. This allows the ESP microcontroller to remain in deep sleep until motion is detected.

## Project Objectives

- Develop a compact ESP-based wireless camera node.
- Design a PIR motion detection circuit using operational amplifiers and signal conditioning.
- Implement interrupt-driven wake-up from deep sleep.
- Establish wireless video transmission to a Raspberry Pi cluster.
- Implement centralised computer vision, recording, and monitoring.
- Evaluate system power consumption, detection reliability, and communication performance.

## System Architecture

The system is divided into three primary subsystems.

### 1. ESP Camera Node

Responsible for:

- Camera interfacing and video acquisition.
- Wireless communication with the Raspberry Pi cluster.
- Managing sleep and wake-up states.
- Coordinating motion-triggered recording.

### 2. PIR Motion Detection Circuit

A custom analogue circuit designed to detect motion while maintaining minimal standby power consumption.

The circuit will incorporate:

- PIR sensor signal acquisition.
- Operational amplifier-based signal amplification.
- Analogue filtering to reduce noise and false triggering.
- Threshold detection using a comparator.
- Digital interrupt output to wake the ESP microcontroller.

The PIR detection circuit will remain powered while the ESP is in deep sleep.

### 3. Raspberry Pi Processing Cluster

Responsible for:

- Receiving video streams and event data.
- Performing computer vision and object detection.
- Managing recording and storage.
- Providing centralised security monitoring.

## Hardware

| Component | Purpose |
|---|---|
| ESP Microcontroller | Camera control, wireless communication, and power management |
| Camera Sensor | Image and video acquisition |
| PIR Sensor | Low-power motion detection |
| Operational Amplifier | PIR signal amplification and filtering |
| Comparator | Digital motion detection output |
| Raspberry Pi Cluster | Video processing, storage, and monitoring |
| Power Management Circuit | Regulated power supply and low-power operation |

## Software and Technologies

- **C/C++** — ESP firmware development
- **Python** — Raspberry Pi processing
- **ESP-IDF** — Embedded firmware and power management
- **OpenCV** — Computer vision
- **LTspice** — Analogue circuit simulation
- **KiCad** — Schematic capture and PCB design
- **Git / GitHub** — Version control and project management

## Development Plan

1. Select the ESP microcontroller, camera sensor, and PIR sensing element.
2. Design and simulate the PIR amplifier, filtering, and comparator circuit.
3. Prototype and validate the motion detection circuit.
4. Implement ESP deep-sleep and PIR-triggered wake-up functionality.
5. Establish camera capture and wireless transmission.
6. Develop Raspberry Pi video reception and processing.
7. Test power consumption, motion detection reliability, and system performance.

## Future Development

- Multiple wireless camera nodes.
- Distributed processing across the Raspberry Pi cluster.
- Custom PCB integration and compact enclosure design.
- Battery-powered operation and improved power efficiency.
- Advanced computer vision and automated notifications.

## Project Status

**Planning and Initial Development**

Current development is focused on defining the system architecture, selecting hardware, and designing the low-power PIR motion detection subsystem.
