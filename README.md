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

## Hardware Architecture

The system uses a distributed architecture with a low-power wireless camera node and a central Raspberry Pi processing cluster.

| Component | Selection | Function |
|---|---|---|
| Main processor | ESP32-P4 | Camera control and video encoding |
| Wireless processor | ESP32-C6 | 2.4 GHz Wi-Fi 6 communication |
| Development camera | Raspberry Pi Camera Module 3 | Initial camera testing |
| Final camera | Raspberry Pi Camera Module 3 NoIR | Infrared-sensitive video capture |
| Motion detection | PIR sensor | Detect motion during standby |
| Signal conditioning | Custom op-amp and comparator circuit | Amplify, filter and digitise the PIR signal |
| Night vision | IR LED illuminator | Illuminate the scene in darkness |
| Processing | Raspberry Pi 5 cluster | Video analysis, recording and storage |
| PCB | Custom-designed PCB | Hardware integration and power management |

### System Operation

1. The PIR detection circuit remains active while the camera node is in deep sleep.
2. Detected motion generates a wake-up signal for the ESP32-P4.
3. The ESP32-P4 activates the camera and captures video.
4. The ESP32-C6 transmits video over Wi-Fi to the Raspberry Pi cluster.
5. The Raspberry Pi cluster processes and stores the footage.
6. The camera node returns to deep sleep after completing the event.

**Design status:** Component architecture selected. Electrical design and performance validation are pending.

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
