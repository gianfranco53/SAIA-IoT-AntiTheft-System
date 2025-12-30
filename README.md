# SAIA-IoT-AntiTheft-System
Smart Automotive Intelligent Anti-theft System – IoT proof-of-concept
# SAIA – Smart Automotive Intelligent Anti-theft System

## Overview
SAIA is a proof-of-concept intelligent vehicle anti-theft system based on IoT technologies.
The project was developed to overcome the limitations of traditional car alarms by introducing
a secure, low-power, event-driven architecture with remote control capabilities.

The system has been designed and tested in real-world conditions on a private vehicle.

## Key Features
- Intelligent remote engine immobilization with safety logic (vehicle stopped only)
- Event-driven GPS tracking (no continuous polling)
- ESP32-based control unit with EEPROM state persistence
- Android-based tracker with kiosk-mode anti-tampering protection
- Telegram-based real-time alerts
- Ultra-low power consumption architecture
- No cloud dependency

## System Architecture
SAIA consists of:
- ESP32 microcontroller acting as control unit and Bluetooth server
- Android smartphone used as GPS tracker and communication gateway
- Automotive relay / MOSFET for engine immobilization
- SMS and Telegram for command and alert channels

The architecture is designed to minimize power consumption and maximize operational safety.

## Safety Considerations
Engine immobilization is executed only when the vehicle is confirmed to be stationary.
This prevents dangerous or unintended shutdowns while driving.

## Project Status
- Fully functional prototype
- Tested in real usage scenarios
- Minor software refinements in progress
- Not certified for commercial automotive use

## Intended Use
This repository is published as a technical proof-of-concept.
It is not intended for direct consumer use or installation.

## Commercial & Industrial Interest
The author is open to discussions regarding:
- Industrial partnerships
- Licensing agreements
- Technical collaborations
- Product industrialization

The project is aimed at companies operating in:
- Automotive security systems
- IoT devices
- Fleet management solutions
- Anti-theft and insurance technologies

Developed by a senior multidisciplinary technician with a background in mechanics,
electronics and software development, and decades of hands-on experience in
electro-informatics and embedded systems.

## Disclaimer
This project is provided for research and evaluation purposes only.
The author assumes no responsibility for improper use or installation.

