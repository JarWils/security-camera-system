# Hardware Component Selection

## Main Processing and Communication

| Component | Selection | Status |
|---|---|---|
| Video processor | ESP32-P4 | Selected |
| Wi-Fi processor | ESP32-C6 | Selected |
| Camera sensor | Sony IMX708 | Selected |
| Development camera | Camera Module 3 | Owned |
| Final camera | Camera Module 3 NoIR | Planned |
| Processing server | Raspberry Pi 5 cluster | Planned |

## Motion Detection Circuit

| Component | Selection | Status |
|---|---|---|
| PIR sensor | TBD | Not selected |
| Operational amplifier | TBD | Not selected |
| Comparator | TBD | Not selected |
| Analogue filters | TBD | Design pending |

## Power Management

| Component | Selection | Status |
|---|---|---|
| Power source | TBD | Not selected |
| Voltage regulators | TBD | Not selected |
| Power switching | TBD | Design pending |
| IR LEDs | TBD | Not selected |

## Communication

- Wireless: 2.4 GHz Wi-Fi 6
- P4 to C6: SDIO (proposed)
- Camera to P4: MIPI CSI-2
- Video processing: Raspberry Pi cluster

## Design Notes

The final system will be integrated onto a
custom PCB.

Component selections remain subject to
electrical, software and power validation.
