# Security Camera System — Hardware Components

## 1. Project Overview

The project aims to develop a compact, low-power wireless security camera using an ESP32-P4 processor and ESP32-C6 wireless microcontroller.

A custom PIR motion detection circuit will monitor for movement while the camera system remains in deep sleep. When motion is detected, the ESP32-P4 will wake, activate the camera and transmit video through the ESP32-C6 to a Raspberry Pi 5 processing cluster.

The hardware will ultimately be integrated onto a custom-designed PCB.

## 2. Main Processing and Communication

| Component | Part / Model | Purpose | Status |
|---|---|---|---|
| Main processor | ESP32-P4 | Camera control, video capture and H.264 encoding | Selected |
| Wireless microcontroller | ESP32-C6 | 2.4 GHz Wi-Fi 6 communication | Selected |
| Interprocessor interface | SDIO | High-speed communication between P4 and C6 | Proposed |
| Processing platform | Raspberry Pi 5 | Video reception, computer vision and recording | Available |
| Processing cluster | Multiple Raspberry Pi 5 boards | Centralised processing and system management | Planned |

### Design Considerations

- The ESP32-P4 will handle camera interfacing and video processing.
- The ESP32-C6 will provide wireless communication.
- Both microcontrollers will support low-power operating modes.
- The PIR circuit will remain powered during standby.
- The system will support expansion to multiple wireless camera nodes.

## 3. Camera and Night Vision

| Component | Part / Model | Purpose | Status |
|---|---|---|---|
| Development camera | Raspberry Pi Camera Module 3 | Initial camera development and testing | Owned |
| Final camera | Raspberry Pi Camera Module 3 NoIR | Infrared-sensitive security camera | Planned purchase |
| Image sensor | Sony IMX708 | Image and video acquisition | Selected |
| Camera interface | MIPI CSI-2 | Camera-to-ESP32-P4 connection | Proposed |
| Infrared illuminator | IR LEDs — TBD | Night-time illumination | Not selected |
| IR LED driver | TBD | Current regulation and switching | Not selected |
| Camera ribbon connector | FPC connector — TBD | Camera connection to PCB | Not selected |

### Camera Requirements

- Target resolution: 1920 × 1080 pixels
- Target frame rate: 30 fps
- Wireless video transmission
- Infrared night vision
- Event-triggered recording

Camera driver compatibility, frame rate and start-up performance require validation.

## 4. PIR Motion Detection Circuit

The PIR subsystem will use a custom analogue signal-conditioning circuit to detect movement and generate a digital wake-up signal for the ESP32-P4.

### 4.1 Sensor and Analogue Components

| Component | Part / Specification | Purpose |
|---|---|---|
| PIR sensor | Murata IRA-S210ST01 | Detects changes in infrared radiation caused by motion |
| Fresnel lens | Murata IML-0686 | Defines the PIR sensor's detection coverage |
| Quad operational amplifier | Microchip MCP6044 | Amplifies and filters the PIR signal |
| Dual comparator | Microchip MCP6542 | Converts the conditioned signal into a digital wake-up output |
| Resistors | 1 MΩ and other values to be determined | Signal biasing, gain and comparator thresholds |
| Capacitors | 0.33 µF and 0.47 µF candidates; final values to be determined | Analogue filtering and supply decoupling |

Component values and package selections will be finalised during circuit simulation and schematic design.

### 4.2 PIR Circuit Architecture

**Signal path:**

PIR Sensor → Operational Amplifier → Analogue Filtering → Comparator → ESP32-P4 Wake-Up GPIO

### 4.3 Design Requirements

- Target detection range: 5 m
- Continuous low-power motion monitoring
- Amplification of low-level PIR signals
- Band-pass filtering to reduce noise
- Defined motion detection threshold
- Comparator hysteresis to prevent false triggering
- Digital wake-up signal compatible with ESP32-P4 GPIO
- Minimal quiescent current consumption

### 4.4 Development Tasks

- [ ] Review PIR sensor electrical characteristics
- [ ] Determine amplifier gain requirements
- [ ] Calculate filter cutoff frequencies
- [ ] Design comparator threshold and hysteresis
- [ ] Simulate analogue circuitry in LTspice
- [ ] Prototype and test the circuit
- [ ] Measure standby current
- [ ] Integrate the circuit into the final PCB

## 5. Power Management

The security camera will use event-driven power management to minimise standby consumption.

| Component | Selection | Purpose | Status |
|---|---|---|---|
| Main power source | TBD | Supply camera node | Not selected |
| Voltage regulators | TBD | Provide regulated supply rails | Not selected |
| Load switches / MOSFETs | TBD | Control power to camera and peripherals | Not selected |
| Supply decoupling capacitors | TBD | Power supply filtering | Not selected |
| Reverse-polarity protection | TBD | Input protection if required | Not selected |
| Battery management | TBD | Charging and battery protection if applicable | Not selected |

### Power Requirements

- Total camera-node standby current below 1 mA
- Wake-to-first-frame latency below 2 seconds
- PIR sensor and analogue circuit remain continuously powered
- Camera and IR illuminator inactive during standby
- ESP32-P4 and ESP32-C6 use low-power operating states
- Power consumption measured during standby, wake-up and operation

The power architecture and operating voltages will be finalised after determining the power source and component requirements.

## 6. Custom PCB Development

A custom PCB will integrate the ESP32-P4, ESP32-C6, PIR analogue circuitry, camera interface and power management.

| Design Element | Approach | Status |
|---|---|---|
| PCB design software | KiCad | Selected |
| PCB layer count | Four layers initially | Proposed |
| Main processor | ESP32-P4 | Selected |
| Wireless processor | ESP32-C6 | Selected |
| Camera connection | MIPI CSI-2 FPC interface | Proposed |
| Wi-Fi antenna | PCB or external antenna | Undecided |
| PIR analogue front end | MCP6044 + MCP6542 | Selected; circuit design pending |
| Power distribution | Multiple controlled power domains | To be designed |
| Programming / debugging | UART / USB / JTAG as applicable | To be designed |

### PCB Design Considerations

- Controlled-impedance routing for MIPI CSI-2 signals
- Reliable SDIO communication between processors
- Separation of sensitive analogue circuitry and digital/RF circuits
- Low-noise voltage regulation
- Power-domain switching
- RF antenna placement and clearance
- Test points for power, analogue signals and wake-up control
- Programming and debugging interfaces

## 7. Hardware Development Plan

- [ ] Finalise component selection and electrical requirements
- [ ] Design PIR analogue circuit in LTspice
- [ ] Prototype and validate PIR motion detection
- [ ] Verify ESP32-P4 and ESP32-C6 communication
- [ ] Test Raspberry Pi Camera Module 3 with ESP32-P4
- [ ] Implement deep-sleep wake-up control
- [ ] Design the power distribution system
- [ ] Develop KiCad schematic
- [ ] Design custom PCB
- [ ] Assemble and test prototype
- [ ] Validate system performance and power consumption

## 8. Project Status

**Hardware Selection and Initial Circuit Design**

The main processing and wireless microcontrollers have been selected, alongside the camera architecture and core PIR signal-conditioning components.

The next development stage involves finalising the power architecture, simulating the PIR detection circuit and verifying camera compatibility before designing the custom PCB.

All component choices remain subject to electrical and software validation.
