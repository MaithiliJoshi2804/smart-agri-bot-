# 🏗️ System Architecture

End-to-end design of the Smart Agri-Bot system.

## High-Level Flow

```
FIELD ENVIRONMENT
       │
       ▼
┌─────────────────────────────┐
│        SENSOR LAYER         │
│  Soil Moisture │ DHT11      │
└────────────┬────────────────┘
             │ Raw sensor readings
             ▼
┌─────────────────────────────┐
│      PROCESSING LAYER       │
│         Arduino             │
│   AI Decision Algorithm     │
│  (threshold-based adaptive) │
└──────┬──────────────┬───────┘
       │              │
       ▼              ▼
┌────────────┐  ┌───────────────┐
│ IRRIGATION │  │ SEED SOWING   │
│ Water Pump │  │ Mechanism     │
│ + Relay    │  │ (depth-aware) │
└────────────┘  └───────────────┘
       │
       ▼
┌─────────────────────────────┐
│      WIRELESS LAYER         │
│           ESP32             │
│  Data logging & telemetry   │
└─────────────────────────────┘
       │
       ▼
┌─────────────────────────────┐
│      MOBILITY LAYER         │
│  DC Motors + Motor Driver   │
│  4-wheel chassis on soil    │
└─────────────────────────────┘
```

## Component Roles

### Arduino (Brain)
- Reads all sensor inputs
- Runs the AI decision algorithm
- Controls all outputs (pump, seed mechanism, motors)
- Communicates with ESP32 over serial

### ESP32 (Communications)
- Receives data from Arduino
- Logs sensor readings and actions wirelessly
- Enables remote monitoring capability

### Sensor Layer
- **Soil Moisture Sensor** → tells the bot how dry/wet the soil is
- **DHT11** → provides temperature and humidity context for decisions

### Actuation Layer
- **Water Pump + Relay** → physical irrigation execution
- **Seed Mechanism** → deploys seeds at AI-calculated depth
- **DC Motors** → moves the robot forward across the field autonomously

## Feedback Loop

After every action (irrigation or seeding), the bot re-reads sensors before the next decision cycle. This closed-loop design ensures the robot responds to actual field conditions rather than assumptions.
