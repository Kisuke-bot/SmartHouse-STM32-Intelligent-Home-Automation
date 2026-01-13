

---

# 🏠 SmartHouse-STM32: Intelligent Home Automation

**SmartHouse-STM32** is an embedded monitoring system built on the **STM32F446RET (Otak Kecil Board)**. It features real-time environmental sensing, automated street lighting, and a weather-responsive alarm system—all managed through high-performance interrupt-driven logic.

---

## ✨ Key Features

* **Dual-Sensor Intelligence** – Seamlessly integrates an Analog/Digital Light Sensor and Rain Sensor.
* **Automated Street Lighting** – Intelligent LED control (Pins PA8–PA11) based on ambient light levels.
* **Real-Time Weather Alerts** – Instant audible (Buzzer) and visual (Red LED) notifications when rain is detected.
* **Hardware Interrupt Override** – Uses **EXTI14** to provide a manual lighting override, ensuring user control at all times.
* **Smart Mute Logic** – A dedicated mute button (PC13) silences the alarm while maintaining visual safety warnings.
* **Low-Level Optimization** – Utilizes **BSRR** and **IDR** registers for atomic, ultra-fast hardware response.

---

## 🛠 How It Works

1. **Sensing Stage** – The system polls the environment. The light sensor determines the Day/Night cycle, while the rain sensor monitors for moisture.
2. **Logic Processing** – The STM32 calculates state transitions. It uses **XOR Logic** to combine sensor data with the user's manual override status.
3. **Actuation Stage** – It updates the **I2C 16×2 LCD** with status strings ("WEATHER: RAIN", "STATUS: DAY") and triggers physical actuators like the buzzer and LEDs.
4. **Interrupt Handling** – Pressing the PC14 button triggers an asynchronous interrupt, instantly flipping the light state without stopping the main program.

---

## 📊 Logic & Feedback Table

| Input Condition | LED Status (PA8-11) | Buzzer / Red LED | LCD Display |
| --- | --- | --- | --- |
| **☀️ Day Mode** | 🌑 OFF | 🔇 Silent | `STATUS: DAY` |
| **🌙 Night Mode** | 💡 ON | 🔇 Silent | `STATUS: DARK` |
| **🌧 Rain Detected** | (Sensor Based) | 🔊 ON / 🔴 ON | `WEATHER: RAIN` |
| **🔘 Manual OVR** | 🔄 Toggled | (No Change) | `[OVR ON]` |

---

## 🚀 Potential Upgrades

* **IoT Integration** – Add an **ESP8266** or **ESP32** module to send weather alerts to a mobile app via Wi-Fi.
* **Servo Control** – Add a motor to automatically close a window or "roof" when the rain sensor is triggered.
* **Analog Sensitivity** – Use **ADC (Analog-to-Digital Converter)** to adjust LED brightness gradually based on the exact light level.
* **Data Logging** – Export sensor history to an SD card for environmental analysis.

---

## 🎯 Why This Project?

* **Industrial Standard** – Uses the STM32F4 series, a powerful ARM Cortex-M4 chip used in professional engineering.
* **Interrupt Mastery** – Demonstrates how to handle real-time user inputs without polling lag.
* **Atomic Control** – Learn to manipulate hardware registers directly for maximum efficiency.

---

## 💡 Ideal For

* **Engineering Students** learning ARM Cortex-M4 architecture.
* **Makers** building reliable, high-speed home automation prototypes.
* **STM32 Enthusiasts** exploring I2C, EXTI, and GPIO register control.

---

