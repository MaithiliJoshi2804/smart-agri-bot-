# 🌾 Smart Agri-Bot — Autonomous Precision Agricultural Robot

> **IEEE ICCSP 2025 Published Research · 1st Place, College-Level Competition**

An IoT-enabled autonomous agricultural robot that moves across soil terrain, reads live sensor data, and uses AI decision-making to automate irrigation and precision seed sowing — with zero manual intervention.

---

## 🎥 Demo & Showcase

👉 **[View Live Project Showcase](https://yourusername.github.io/smart-agri-bot)**

> _(Replace `yourusername` with your GitHub username after enabling GitHub Pages)_

---

## 🤖 What It Does

The Smart Agri-Bot is a self-driving robot (car-like chassis) that navigates across a field and:

- 📡 **Reads real-time sensor data** — soil moisture, temperature, humidity
- 🧠 **Makes AI-driven decisions** — when to irrigate, how deep to sow seeds
- 💧 **Automates irrigation** — activates water pump based on soil moisture levels
- 🌱 **Precision seed sowing** — deploys seeds at optimal depth based on sensor readings
- 🔄 **Self-corrects** — post-action readings feed back into the decision loop

---

## 🏆 Recognition

| Achievement | Details |
|-------------|---------|
| 🥇 Competition | **1st Place** — College-Level Robotics & AI Competition |
| 📄 Publication | **IEEE ICCSP 2025** — Peer-reviewed conference paper |
| 🔬 Research | Co-authored paper on AI-integrated IoT agricultural systems |

---

## 🛠️ Hardware Components

| Component | Purpose |
|-----------|---------|
| **Arduino** | Core microcontroller — runs decision logic and controls actuators |
| **ESP32** | Wi-Fi/Bluetooth module — handles wireless data transmission |
| **Soil Moisture Sensor** | Measures real-time soil water content |
| **DHT11 Sensor** | Reads temperature and humidity from the environment |
| **DC Motors + Motor Driver** | Drives the robot chassis across soil terrain |
| **Water Pump + Relay** | Activates irrigation based on AI decision |
| **Seed Sowing Mechanism** | Deploys seeds at precise depth |
| **Robot Chassis (Car frame)** | 4-wheel drive frame for field navigation |
| **Power Supply (Battery)** | Powers the entire system autonomously |

---

## ⚙️ System Architecture

```
[Soil Moisture Sensor] ──┐
[DHT11 Temp/Humidity]  ──┤──► [Arduino Microcontroller]
[Other Field Sensors]  ──┘         │
                                    ▼
                          [AI Decision Algorithm]
                          ┌─────────┴─────────┐
                          ▼                   ▼
                   [Irrigation ON/OFF]  [Seed Deployment]
                   (Water Pump)         (Sowing Mechanism)
                          │
                          ▼
                   [ESP32 — Data Logging & Wireless]
```

---

## 🧠 AI Decision Logic

The onboard AI algorithm works on threshold-based adaptive logic:

```
IF soil_moisture < threshold_low:
    activate_irrigation()
    log_event("Irrigation triggered")

IF soil_moisture >= threshold_optimal:
    deactivate_irrigation()

IF temperature in optimal_range AND moisture == optimal:
    trigger_seed_sowing(depth=calculated_depth)

LOOP: re-read sensors → re-evaluate → act
```

The thresholds were tuned through multiple field test cycles to account for real-world soil and weather variability.

---

## 📁 Repository Structure

```
smart-agri-bot/
├── README.md                  ← You are here
├── index.html                 ← Live project showcase (GitHub Pages)
│
├── hardware/
│   └── components.md          ← Full component list with specs
│
├── code/
│   └── decision_logic.md      ← AI decision algorithm (pseudocode + explanation)
│
├── docs/
│   ├── system_architecture.md ← End-to-end system design
│   └── ieee_paper_reference.md← IEEE ICCSP 2025 paper citation
│
└── media/
    └── (photos & videos of robot, field tests, competition)
```

---

## 📸 Media

> Photos and videos of the robot in action, field tests, and competition are in the [`/media`](./media) folder.

---

## 👩‍💻 Team & Author

**Maithili Sadashiv Joshi** — AI & Software Logic, System Integration, Frontend Dashboard
KLE Technological University, Belagavi | B.E. Computer Science with AI (2022–2026)

- 🔗 [LinkedIn](https://linkedin.com/in/maithilijoshi28)
- 📧 maithilijoshi2804@gmail.com

---

## 📄 Publication

**Conference:** IEEE ICCSP 2025
**Title:** Smart Agri-Bot — AI-Integrated IoT Approach for Autonomous Agricultural Systems
**Status:** Peer-reviewed, published

---

## 📜 License

This project is for academic and research purposes.
