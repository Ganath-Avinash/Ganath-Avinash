<h1 align="center">Ganath Avinash G R</h1>

<p align="center">
  <a href="https://git.io/typing-svg">
    <img
      src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&pause=1000&color=58A6FF&center=true&vCenter=true&width=950&lines=B.Tech+CSE+%C2%B7+Full-Stack+Developer+%C2%B7+AI+Agent+Builder;Amrita+Vishwa+Vidyapeetham%2C+Chennai+Campus;Building+real+software+with+AI+and+modern+web+technologies."
      alt="Typing SVG"
    />
  </a>
</p>

## About

I am a third-year Computer Science student at Amrita Vishwa Vidyapeetham focused on full-stack software engineering and applied AI systems. My work centers on building scalable web applications, modern user interfaces, and task-specific AI agents that integrate into real-world workflows.

I am particularly interested in practical applications of language models, retrieval systems, backend engineering, and AI-driven automation. My goal is to build production-grade software that combines strong engineering principles with intelligent systems.

**Current areas of focus:**
- Full-stack application development
- AI agent architecture and orchestration
- Backend systems and API design
- Retrieval-Augmented Generation (RAG)
- Modern frontend engineering and responsive UI systems


## Tech Stack

<p>
  <img src="https://skillicons.dev/icons?i=py,js,ts,react,nextjs,nodejs,express,java,cpp,mysql,mongodb,html,css,tailwind,langchain&theme=dark" />
</p>


## Coding Stats

<p>
  <a href="https://leetcode.com/Ganath" target="_blank">
    <img src="https://img.shields.io/badge/LeetCode-Ganath-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" />
  </a>
  &nbsp;
  <a href="https://www.hackerrank.com/profile/ganathavinash_gr" target="_blank">
    <img src="https://img.shields.io/badge/HackerRank-ganathavinash__gr-2EC866?style=for-the-badge&logo=hackerrank&logoColor=white" />
  </a>
  &nbsp;
</p>

<p>
  <a href="https://leetcode.com/Ganath" target="_blank">
    <img src="https://leetcard.jacoblin.cool/Ganath?theme=dark&font=Fira%20Code&ext=heatmap" width="500"/>
  </a>
</p>




## Badges

<table>
  <tr>
    <td align="center" width="150">
      <img src="assets/badges/2_GEMINI_BADGE.png" height="120" width="100" alt="Gemini Certified University Student" style="padding:15px"/><br/>
      <b>University Student</b><br/>
      <sub>Google Gemini</sub>
    </td>
    <td align="center" width="150">
      <img src="assets/badges/3_GEMINI_BADGE_EDU.png" height="120" width="100" alt="Gemini Certified Educator style="padding:15px"/><br/>
      <b>Educator</b><br/>
      <sub>Google Gemini</sub>
    </td>
    <td align="center" width="150">
      <img src="assets/badges/13_GEN-AI-INACTION.png" height="100" width="100" alt="IBM Gen AI in Action style="padding:15px"/><br/>
      <b>Gen AI in Action</b><br/>
      <sub>IBM</sub>
    </td>
  </tr>
</table>



## Projects

| Project | Description | Stack |
|---|---|---|
| [TrafficSense](https://github.com/Ganath-Avinash) | Real-time vehicle emission monitoring and visualization platform | Haskell, JavaScript |
| [RAG Customer Agent](https://github.com/Ganath-Avinash) | Retrieval-Augmented Generation based AI assistant for automated customer support workflows | Python, LangChain, RAG |
| [Portfolio Website](https://ganath-avinash.github.io/PortFolio_GR/) | Personal portfolio showcasing technical projects and engineering work | React, Tailwind CSS |
| [Wits & Bytes](https://github.com/Ganath-Avinash) | Wallpaper discovery and download platform with a responsive frontend and backend integration | React, Node.js, Express |


## Contribution Graph

<p>
  <img src="https://streak-stats.demolab.com?user=Ganath-Avinash&theme=dark&hide_border=true" width="450"/>
</p>

<p>
  <img src="https://raw.githubusercontent.com/Platane/snk/output/github-contribution-grid-snake-dark.svg" alt="Snake animation" />
</p>


## Contact

- **Email:** ganathavinash.gr@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/ganath-avinash/
- **Portfolio:** https://ganath-avinash.github.io/PortFolio_GR/
- **LeetCode:** https://leetcode.com/Ganath

---

<p align="center">
  Building production-focused software with modern engineering and applied AI.
</p>


# SentryX — Project Status & Product State Document
**Document Name:** `State_Now.md`  
**Generated:** October 2026  
**System Version:** Production Firmware v4.5 / Companion App v1.0  
**Target Architecture:** ESP32-WROOM-32 + React/Vite Companion App + Android APK  

---

## 1. Executive Summary

| Domain | Status | Completion | Notes |
| :--- | :--- | :---: | :--- |
| **ESP32 Firmware Logic** | ✅ **COMPLETE** | 100% | TinyML model, FreeRTOS tasks, BLE, GPS, Debouncing, Actuators |
| **Firmware Dual Sync** | ✅ **COMPLETE** | 100% | `hardware.ino` and `SentryX/SentryX.ino` are 100% identical |
| **Web Companion App** | ✅ **COMPLETE** | 100% | Real-time telemetry, Leaflet Map, SOS HUD, Contacts NVS sync |
| **Android APK** | ✅ **COMPLETE** | 100% | `SentryX-Companion.apk` (15.08 MB) compiled with native BLE |
| **USB Serial & Web BLE** | ✅ **COMPLETE** | 100% | Works via COM7 (115200 baud) and Web Bluetooth |
| **SIM800L Cellular Dispatch** | ⚠️ **BENCH READY** | 80% | Firmware is 100% written; requires 2A power rail & 2G SIM |
| **Hardware Enclosure (Casing)** | ⏳ **PENDING** | 0% | Physical housing, antenna orientation & chassis mounting |

---

## 2. What Has Been Completed (100% Done)

### A. Embedded Firmware (ESP32 Core)
1. **Dual Core FreeRTOS Task Architecture**:
   * **Core 1 (High Priority)**: `imuTask` (200 Hz physical sampling, MPU6050 6-axis I2C DMA, ring buffer), `classifyTask` (1 Hz TinyML decision trees).
   * **Core 0 (Background)**: `gpsTask` (UART2, 9600 baud NMEA parsing), `simSerial` (UART1, 9600 baud GSM control).
2. **TinyML Crash Detection & Anomaly Suppression**:
   * Binary classification (Crash vs Normal) trained on 24 statistical features (SMA, Jerk, Variance, Tilts).
   * Multi-class classification for potholes and hard braking.
   * **Post-impact stillness cascade** (1-second stillness window $\ge 0.40$) prevents false triggers from cornering.
   * **Desk Noise Fix**: Dynamic motion barrier (`SMA > 12.0` or `Jerk > 30.0`) stops stationary desk sensor noise from triggering road anomalies or infinite 2-second buzzing loops.
3. **Actuator & Sound Management**:
   * **Road Anomalies (Pothole / Braking)**: Buzzer is **muted**; alerts use a clean, non-blocking 350 ms Red LED pulse.
   * **Crash Event**: High-priority alarm buzzer sounds during the 30-second countdown with fast Red LED flashing.
   * **System Normal**: Green LED pulses gracefully when BLE is connected.
4. **Hardware Push-Button (GPIO 14)**:
   * Configured with internal pullup (`INPUT_PULLUP`) and hardware debouncing.
   * **From any normal state**: Triggers instant simulated crash demo for checking actuators, telemetry, and app response.
   * **During active countdown**: Instantly cancels the emergency countdown (`I'M OK` override).
   * **After SOS dispatch**: Resets system state back to `STATE_NORMAL`.
5. **NimBLE 1.x & NimBLE 2.x Dual-Compatibility**:
   * Automatic macro detection (`#if SENTRYX_NIMBLE_V2`) supports legacy NimBLE and NimBLE 2.5.1+ without compiler `override` errors.
6. **Live GPS Data Stream**:
   * UART2 on pins 32 (RX) and 33 (TX).
   * Live latitude, longitude, satellite count, and speed streaming.
   * Hardcoded Chennai coordinates completely removed (defaults to `0.0f, 0.0f` until locked).
   * Dynamic Google Maps URL formatting: generates active link when satellite fix exists, or clear status when acquiring.
   * Remote GPS synchronization support via serial/BLE (`GPS:lat,lng`).
7. **Simulated SIM800L Bench Mode**:
   * If physical GSM hardware is absent, firmware switches to simulated mode and outputs the full formatted SMS dispatch to the serial monitor without freezing.
8. **Firmware Synchronization**:
   * Both [`hardware_test/hardware.ino`](file:///c:/Main/College/College_Stuff/SEM-5/EMB/Project/Project-2W/hardware_test/hardware.ino) and [`hardware_test/SentryX/SentryX.ino`](file:///c:/Main/College/College_Stuff/SEM-5/EMB/Project/Project-2W/hardware_test/SentryX/SentryX.ino) are strictly identical and Arduino IDE ready.

---

### B. Companion App & Mobile APK
1. **Web Dashboard & Hardware Features**:
   * Dynamic G-Force HUD, Roll/Pitch gauges, Speedometer, and Satellite count indicator.
   * Raw IMU stream table (Ax, Ay, Az, Gx, Gy, Gz, SMA, Jerk, Stillness).
   * Serial COM7 connection via Web Serial API and BLE connectivity via Web Bluetooth.
2. **Live GPS Map & Indoor Bypass**:
   * Leaflet OpenStreetMap with dark AMOLED mode.
   * Zero hardcoded Chennai fallbacks: displays **`SEARCHING (0 SATS)`** and **`Searching for Satellites...`** when indoors.
   * **`Sync Phone GPS`** button allows injecting mobile phone GPS coordinates into the ESP32 for indoor demos.
   * Automatically locks onto live satellite coordinates when outdoors.
3. **Emergency SOS Countdown HUD**:
   * Fullscreen red overlay with 30-second circular SVG countdown timer.
   * Web Audio siren generator.
   * Prominent **`I'M OK — CANCEL SOS`** button.
   * Emergency dispatch confirmation screen listing 108 Ambulance, user contacts, and live Google Maps location.
4. **Android Native Build**:
   * Android BLE permissions (`android:usesPermissionFlags="neverForLocation"`, `BLUETOOTH_SCAN`, `BLUETOOTH_CONNECT`, `ACCESS_FINE_LOCATION`) configured in AndroidManifest.
   * Production APK compiled: [`SentryX-Companion.apk`](file:///c:/Main/College/College_Stuff/SEM-5/EMB/Project/Project-2W/SentryX-Companion.apk) (15.08 MB) located in project root.

---

## 3. What Is Remaining (Physical & Field Verification)

```
┌────────────────────────────────────────────────────────────┐
│                    REMAINING MILESTONES                    │
├──────────────────────────┬──────────────────┬──────────────┤
│ Milestone                │ Difficulty       │ Status       │
├──────────────────────────┼──────────────────┼──────────────┤
│ 1. SIM800L Hardware Check│ Medium (Power)   │ Needs Test   │
│ 2. Outdoor GPS Lock Test │ Easy (Field)     │ Needs Test   │
│ 3. Physical Enclosure    │ Mechanical       │ Pending      │
└──────────────────────────┴──────────────────┴──────────────┘
```

### Milestone 1: SIM800L Hardware Check & Power Verification
The firmware logic for AT commands, network checking, SMS creation, and Ctrl+Z submission is **100% complete**. However, the physical SIM800L module has strict electrical requirements:

1. **Power Supply Requirement (Crucial)**:
   * **Problem**: SIM800L operates at **3.7V – 4.2V** (optimal 4.0V) and requires up to **2.0 Amps peak current** during cellular radio transmission bursts.
   * **Warning**: You **cannot** power SIM800L directly from the ESP32 3.3V or 5V pin! Doing so causes the SIM800L to brown-out, reset, or blink rapidly in a reboot loop.
   * **Solution**: Power SIM800L from a dedicated single-cell 18650 Li-ion battery (3.7V–4.2V) or an external buck converter (e.g., LM2596 tuned to 4.0V) with a **1000 µF capacitor** soldered across SIM800L `VCC` and `GND`.
   * **Common Ground**: Ensure the external power GND is connected to the ESP32 GND.
2. **SIM Card Compatibility**:
   * SIM800L is a **2G GSM** modem.
   * In India, use an **Airtel** or **Vodafone-Idea (Vi)** SIM with 2G fallback and an active SMS plan.
   * **Do NOT use Jio**: Jio is an LTE/VoLTE-only network with no 2G GSM infrastructure.
3. **LED Diagnostic Pattern on SIM800L**:
   * *Blinking every 1 second*: Searching for network (Not registered yet).
   * *Blinking every 3 seconds*: **Registered on cellular network (Ready to send SMS)**.
   * *Blinking fast (every 800ms)*: GPRS data mode.

---

### Milestone 2: Outdoor GPS Lock Test
1. **Take the unit outdoors**: NEO-6M radio signals (-160 dBm) cannot penetrate concrete roofs or metal slabs.
2. **Ceramic Antenna Orientation**: The ceramic square antenna **must face flat toward the open sky**.
3. **Cold Start Time**: Allow **45 to 90 seconds** on fresh power-up for satellite ephemeris download.
4. **Success Indicator**: The tiny **1PPS red LED** on the NEO-6M board will start **blinking at 1 Hz (once per second)**. As soon as it blinks, live coordinates stream to the ESP32 and companion app.

---

### Milestone 3: Hardware Casing & Enclosure
A two-wheeler safety system requires mechanical protection from vibration and weather:

1. **Enclosure Specifications**:
   * Recommended: Weatherproof ABS/Polycarbonate project box (e.g., 100mm × 68mm × 50mm).
   * Non-metallic lid: GPS ceramic antenna must be positioned directly underneath the plastic lid (never metal).
2. **Internal Component Arrangement**:
   * **MPU6050 Mounting**: Must be rigidly mounted/screwed to the baseplate so motorcycle roll and vibration are directly transferred to the accelerometer.
   * **SIM800L Antenna**: Position the spring/helical antenna away from the MPU6050 I2C wires to prevent GSM radio burst induction.
   * **Faceplate**: Cutouts for:
     * Red LED (Impact / Countdown alert)
     * Green LED (BLE connection status)
     * Push Button (Demo trigger / Emergency cancel)
     * Buzzer sound vent
     * USB Type-C / Micro-USB port for charging or serial telemetry

---

## 4. Hardware Wiring Reference Sheet

| Peripheral | ESP32 GPIO | Peripheral Pin | Notes |
| :--- | :--- | :--- | :--- |
| **MPU6050** | GPIO 21 | SDA | I2C Data (Internal pullup) |
| | GPIO 22 | SCL | I2C Clock |
| | GPIO 27 | INT | Motion Interrupt |
| | 3.3V / GND | VCC / GND | Power rail |
| **NEO-6M GPS** | GPIO 32 | TX (GPS) | UART2 RX (ESP32 receives NMEA) |
| | GPIO 33 | RX (GPS) | UART2 TX |
| | 3.3V / 5V | VCC / GND | Power rail |
| **SIM800L GSM** | GPIO 4 | TX (SIM) | UART1 RX (ESP32 receives AT response) |
| | GPIO 26 | RX (SIM) | UART1 TX (ESP32 sends AT commands) |
| | **External 4V 2A**| VCC / GND | **Do NOT power from ESP32 pins!** |
| | Common GND | GND | Connect to ESP32 GND |
| **Buzzer** | GPIO 25 | (+) Pin | Piezo active buzzer (Muted for road bumps) |
| **Red LED** | GPIO 18 | Anode (+) | 220Ω resistor to GND |
| **Green LED** | GPIO 19 | Anode (+) | 220Ω resistor to GND |
| **Button** | GPIO 14 | Button Pin 1 | Other pin to GND (`INPUT_PULLUP`) |

---

## 5. Summary Checklist Before Demo / Evaluation

- [x] Flash [`hardware_test/SentryX/SentryX.ino`](file:///c:/Main/College/College_Stuff/SEM-5/EMB/Project/Project-2W/hardware_test/SentryX/SentryX.ino) onto the ESP32.
- [x] Sideload [`SentryX-Companion.apk`](file:///c:/Main/College/College_Stuff/SEM-5/EMB/Project/Project-2W/SentryX-Companion.apk) on Android phone or open Web Dashboard on Chrome (COM7 Serial / BLE).
- [x] Press the hardware button on GPIO 14: Verify instant simulated crash countdown, siren sound, and companion app HUD.
- [x] Press the button again within 30 seconds: Verify clean cancellation (`I'm OK`).
- [x] Test simulated SMS: Verify formatted SMS output with live GPS coordinates in Serial monitor.
- [ ] Connect external 3.7V–4.2V 2A power to SIM800L with 2G SIM card and verify network registration (LED blinks every 3s).
- [ ] Take hardware outside under open sky and verify NEO-6M 1PPS LED blinks at 1 Hz.
- [ ] Fit components into 3D-printed or project enclosure.

