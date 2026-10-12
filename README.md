# 🚀 mOS (Micro Operating System)

> A minimalist, dual-architecture custom firmware and micro-UI for BBC micro:bit v1/v1.5 and v2.  
> **Developed by PROBE**

---

## 📌 About mOS
**mOS** is an independent, lightweight mini-operating system engineered specifically for BBC micro:bit microcontrollers. Built from the ground up to bypass stock limitations, mOS brings a clean, PCB-inspired minimalist interface, custom boot sequences, system diagnostic tools, and retro arcade games directly to your 5x5 LED matrix.

---

## ⚡ Latest Release Information

### **Current Version:** `mOS Pixel SL Edition (v1.1)`
- **Status:** Stable Release / Universal Optimized Build
- **Release Target:** Cross-Architecture Telemetry & Scratch Integration

### 🧩 Hardware Compatibility Matrix

| Version / Edition | Supported Hardware | Processor | Memory Limit | Audio Support | Touch Logo | SL App Support |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **mOS Pixel Alpha** | BBC micro:bit v1 / v1.5 | Nordic nRF51822 | 16 KB RAM | External Buzzer | No | No |
| **mOS Pixel Pro** | BBC micro:bit v2 | Nordic nRF52833 | 128 KB RAM | Onboard Speaker | Yes | No |
| **mOS Pixel SL Edition** | BBC micro:bit v1 / v1.5 / v2 | Universal | Fully Optimized | Supported (v2) | Supported (v2) | **Yes (Exclusive)** |

---

## 🎮 Features in `mOS Pixel`

- **Minimalist Boot Sequence:** Expanding single-pixel animation leading straight into the mOS startup screen.
- **System Monitor (`SYS` App):** Real-time light level checking and environmental status monitoring.
- **Retro Pong (`PONG` App):** Classic physics-based arcade minigame optimized for the 5x5 LED grid.
- **Scratch Link (`SL` App - *SL Edition Exclusive*):** Real-time telemetry streaming (accelerometer and button states) over serial communication for live integration with Scratch. Available exclusively in the universal SL Edition build.
- **Quick Version Inspector:** Immediate status feedback anywhere in the system.
- **Pro Edition Audio Integration (v2 only):** Interactive sound effects for navigation, wall bounces, and Game Over sequences via the onboard speaker.

---

## 🕹️ System Controls & Navigation

### **In Main Menu:**
- **`Button A`:** Cycle through available applications (`System Monitor` / `Pong` / `SL`*).  
  *\*Note: The `SL` app option is available exclusively when running the mOS Pixel SL Edition firmware.*
- **`Button B`:** Launch the selected application.
- **`Button A + B`:** Display system build info (`mOS v1.5-v1 pixel alpha` or `mOS v2 pixel pro`).
- **`Touch Logo` (v2 Only):** Quick system identity check (`PROBE v2`).

### **Inside Applications:**
- **System Monitor:** Press `A` to read light levels. Press `A + B` to return to the main menu.
- **Retro Pong:** Press `A` to move paddle left, `B` to move paddle right. Press `A + B` to exit to menu.
- **Scratch Link (`SL` - *SL Edition Only*):** Streams live sensor data to computer. Press `A + B` to exit to menu.

---

## 📥 How to Install

1. Download the compiled `.hex` file corresponding to your board version or edition from the links below:
   * [`mOS_Pixel_Alpha_v1.hex`](https://github.com/probeoffical/mOS/releases/latest/download/mOS_Pixel_Alpha_v1.hex) for **v1 / v1.5 (Alpha)**
   * [`mOS_Pixel_Pro_v2.hex`](https://github.com/probeoffical/mOS/releases/latest/download/mOS_Pixel_Pro_v2.hex) for **v2 (Pro)**
   * [`mOS-PİXEL-SL-edition-v1-v15-v2.hex`](https://github.com/probeoffical/mOS/releases/latest/download/mOS-PİXEL-SL-edition-v1-v15-v2.hex) for **Universal SL Edition (Includes SL App)**
2. Connect your BBC micro:bit to your computer via USB.
3. Drag and drop the `.hex` file directly onto the `MICROBIT` drive.
4. Wait for the orange LED on the back to stop flashing.
5. **mOS** will boot up automatically!


## 🕹️ Controls Guide

| Menu / App | Button A | Button B | Button A + B |
| :--- | :--- | :--- | :--- |
| **System Menu** | Cycle / Change Option | Enter / Select App | Exit / Back to Home |
| **PONG Game** | Move Paddle Up / Adjust | Move Paddle Down / Adjust | Exit to Main Menu |
| **Scratch Link (SL)** | Cycle Connection Mode | Initialize / Connect | Exit to Main Menu | 
---

<p align="center">
  <i>mOS is an independent project developed by <b>PROBE</b>.<br>Not affiliated with or endorsed by any other operating system vendors.</i>
</p>
