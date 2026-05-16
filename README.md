# Automated Embedded Thermostat & Fan Controller

An embedded systems project featuring an automated, temperature-controlled cooling fan simulated in Proteus 8. The system monitors ambient temperature via an analog sensor and utilizes software-defined hysteresis logic to dynamically control a cooling fan, maintaining a stable temperature environment.

## 📌 Motivation & Overview
Inspired by a real-world scenario where a lab computer was frequently overheating, this project scales down the problem into a controlled simulation environment. The goal was to build an efficient, automated cooling system that reacts precisely to environmental temperature shifts without causing unnecessary mechanical wear on the cooling components.

---

## 🛠️ Tech Stack & Tools
*   **Language:** C
*   **IDE:** Microchip Studio
*   **Simulation Software:** Proteus 8 Design Suite
*   **Microcontroller:** ATmega32 (easyAVRv7 Board configuration)
*   **Sensors & Components:** LM35 Temperature Sensor, DC Fan, Logic Gates/Drivers

---

## 🚀 Key Features & Engineering Challenges

### 🔹 Software-Defined Hysteresis (The "Buffer Zone")
*   **The Problem:** In a naive thermostat system, setting a target temperature of exactly 50°C causes the fan to rapidly toggle (chatter) on and off if the temperature fluctuates marginally around 49.9°C and 50.1°C. This high-frequency switching degrades hardware rapidly.
*   **The Solution:** Implemented a **4°C Hysteresis Buffer Zone** (48°C - 52°C). 
    *   The fan **turns ON** only when the temperature climbs above **52°C**.
    *   The fan **turns OFF** only when the cooling cycle brings the temperature down below **48°C**.
    *   This prevents rapid oscillation, stabilizes system state transitions, and mimics industrial-grade HVAC logic.

### 🔹 Hardware Interfacing Challenge: Current Amplification
*   **The Challenge:** Microcontroller GPIO pins typically output low current (around 20-40mA), which is insufficient to drive the inductive load of a standard DC cooling fan. 
*   **The Solution:** Integrated a simulated current amplification/driver stage (modeled around a transistor switch/power adapter configuration) to bridge the gap between the low-power ATmega32 control signals and the high-power requirements of the cooling fan motor.

---

## 📸 Simulation & Code Previews

### System Simulation (Proteus 8)
<img width="1026" height="861" alt="image" src="https://github.com/user-attachments/assets/8497be71-f4d7-420d-98a2-c9c7a3c92c9a" />

### Source Code snippet
<img width="1032" height="870" alt="image" src="https://github.com/user-attachments/assets/e9b65f32-934c-41ea-a71c-318ae9d2ee73" />

