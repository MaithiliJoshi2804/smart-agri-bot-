# 🧠 AI Decision Logic

This document explains the core decision-making algorithm running on the Arduino microcontroller.

## Overview

The bot continuously reads sensor data and runs it through a decision algorithm to determine:
1. Whether to irrigate (and for how long)
2. Whether conditions are right for seed sowing
3. What depth to sow seeds at

---

## Pseudocode

```
// ── CONSTANTS (tuned through field testing) ──
MOISTURE_LOW       = 30   // % — trigger irrigation below this
MOISTURE_OPTIMAL   = 60   // % — stop irrigation above this
TEMP_MIN           = 15   // °C — minimum for seed sowing
TEMP_MAX           = 35   // °C — maximum for seed sowing
SEED_DEPTH_DEFAULT = 3    // cm

// ── MAIN LOOP ──
LOOP:
  moisture    = read_soil_moisture_sensor()
  temperature = read_DHT11_temperature()
  humidity    = read_DHT11_humidity()

  // ── IRRIGATION DECISION ──
  IF moisture < MOISTURE_LOW:
    activate_water_pump()
    log("Irrigation ON — moisture: " + moisture + "%")

  ELSE IF moisture >= MOISTURE_OPTIMAL:
    deactivate_water_pump()
    log("Irrigation OFF — moisture optimal")

  // ── SEED SOWING DECISION ──
  IF moisture >= MOISTURE_LOW
  AND temperature >= TEMP_MIN
  AND temperature <= TEMP_MAX:
    depth = calculate_seed_depth(moisture, temperature)
    trigger_seed_sowing(depth)
    log("Seeds sown at depth: " + depth + "cm")

  // ── MOVEMENT ──
  move_robot_forward()

  // ── FEEDBACK LOOP ──
  delay(500)   // re-read sensors every 500ms
  GOTO LOOP


// ── HELPER: Calculate Seed Depth ──
FUNCTION calculate_seed_depth(moisture, temperature):
  IF moisture > 50 AND temperature < 25:
    RETURN 2   // shallow — moist cool soil
  ELSE IF moisture < 40 AND temperature > 28:
    RETURN 4   // deeper — dry warm soil retains moisture deeper
  ELSE:
    RETURN SEED_DEPTH_DEFAULT
```

---

## Why This Logic?

| Condition | Action | Reason |
|-----------|--------|--------|
| Moisture < 30% | Irrigate | Soil too dry for healthy crop growth |
| Moisture ≥ 60% | Stop irrigation | Prevent waterlogging |
| Temp 15–35°C + good moisture | Sow seeds | Optimal germination window |
| Moisture > 50% + temp < 25°C | Shallow sowing (2cm) | Seed accessible to surface moisture |
| Dry + warm | Deep sowing (4cm) | Access deeper moisture reserves |

---

## Threshold Tuning

Thresholds were calibrated through **multiple field test cycles**, adjusting values based on observed plant response and soil behaviour under local Belagavi climate conditions.
