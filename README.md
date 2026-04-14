# Surveillance Camera Car using ESP32-CAM

## Overview
The Surveillance Camera Car using ESP32-CAM is a Wi‑Fi‑controlled robotic vehicle capable of streaming live video and receiving movement commands through a mobile web browser. The system enables remote monitoring of inaccessible or hazardous environments and supports real‑time navigation using an embedded web interface.

This project demonstrates the integration of embedded systems, wireless communication, motor control, and IoT‑based surveillance.

## Features
- Live video streaming over Wi‑Fi
- Remote vehicle control via web browser
- Movement directions: Forward / Backward / Left / Right / Stop
- Motor speed control
- Light intensity control
- Mobile‑friendly control interface

## Applications
- Remote surveillance in restricted or hazardous environments
- Disaster zone monitoring
- Industrial inspection
- Security patrol robots

## Hardware Components
- ESP32‑CAM module (OV2640 camera)
- USB‑to‑serial adapter (or Arduino UNO for passthrough)
- L298N motor driver
- DC motors with chassis
- 7–12 V battery
- Breadboard and jumper wires

## System Architecture
- ESP32‑CAM acts as the Wi‑Fi server, camera stream source, and motor controller interface.
- L298N motor driver controls motor direction and speed (via PWM).
- A mobile browser connects to the ESP32‑CAM to view video and send control commands.

## Working Principle
1. ESP32‑CAM connects to Wi‑Fi.
2. A web server runs on the ESP32‑CAM.
3. The user opens the ESP32 IP address in a browser.
4. The control interface appears with navigation buttons and sliders.
5. Commands are sent to the ESP32‑CAM and motors respond accordingly.
6. Camera streams real‑time video to the interface.

## GPIO Connections

| Signal | GPIO   |
|--------|--------|
| CLK    | GPIO14 |
| CMD    | GPIO15 |
| DATA0  | GPIO2  |
| DATA1 / Flashlight | GPIO4  |
| DATA2  | GPIO12 |
| DATA3  | GPIO13 |

## Uploading Code to ESP32‑CAM
ESP32‑CAM has no onboard USB connector. Use a USB‑to‑serial adapter (or Arduino UNO in passthrough) and follow these connections:

| Adapter / UNO | ESP32‑CAM |
|---------------|-----------|
| RX            | U0T       |
| TX            | U0R       |
| 5V            | 5V        |
| GND           | GND       |
| IO0           | GND (during upload) |

After uploading, disconnect IO0 from GND and reset the ESP32‑CAM.

## Motor Driver Connections
- DC motors connected to L298N outputs
- ESP32‑CAM powered from the motor driver 5V output (or a stable 5V supply)
- External 7–12 V battery connected to L298N input

## Web Interface
The ESP32‑CAM serves a control webpage that includes:
- Direction control buttons
- Speed slider
- Light intensity slider
- Live video stream window

Access the interface via the ESP32 IP address.

## Code Structure
- Motor control functions (direction, stop, PWM speed)
- WebSocket / HTTP handlers for commands
- Embedded HTML/JS served by firmware for the UI
- Camera initialization and frame capture/streaming

## Future Improvements
- Add obstacle detection sensors
- Integrate low‑light / IR illumination
- Implement cloud video storage or streaming
- Provide a dedicated mobile app
- Add autonomous navigation features using onboard sensors

## Conclusion
This project provides a compact, low‑cost surveillance robot capable of wireless monitoring and remote navigation using the ESP32‑CAM platform. It demonstrates practical IoT techniques for embedded video streaming and remote control.