# 🔧 Hardware Components

Complete list of components used in the Smart Agri-Bot system.

## Microcontrollers

| Component | Model | Role |
|-----------|-------|------|
| Microcontroller | Arduino (Uno/Mega) | Core logic, sensor reading, actuator control |
| Wi-Fi Module | ESP32 | Wireless data transmission, remote monitoring |

## Sensors

| Sensor | Model | Measures |
|--------|-------|---------|
| Soil Moisture Sensor | Generic capacitive/resistive | Soil water content (%) |
| Temperature & Humidity | DHT11 | Ambient temp (°C) and humidity (%) |

## Actuators & Mechanical

| Component | Purpose |
|-----------|---------|
| DC Motors (x4) | Drive robot chassis across field terrain |
| Motor Driver (L298N or similar) | Controls motor speed and direction |
| Water Pump (mini submersible) | Activates irrigation on AI command |
| Relay Module | Switches pump ON/OFF based on logic |
| Seed Sowing Mechanism | Deploys seeds at calculated depth |

## Chassis & Power

| Component | Details |
|-----------|---------|
| Robot Chassis | 4-wheel car frame, suitable for uneven soil terrain |
| Battery Pack | Powers entire system autonomously in the field |
| Jumper Wires & Breadboard | Prototyping and connections |

## Wiring Overview

- Sensors → Arduino analog/digital pins
- Arduino → Motor Driver → DC Motors
- Arduino → Relay → Water Pump
- Arduino → ESP32 (Serial communication)
- Battery → Powers Arduino + ESP32 + all peripherals
