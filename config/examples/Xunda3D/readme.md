# 🧰 Xunda3D Custom Marlin Configuration

This repository contains the **custom Marlin firmware configurations** used for the **Xunda 3D Printer**, tailored for African environments and optimized for use with recycled parts and local fabrication capabilities.

---

## 📨 Printer Overview

* **Model:** Xunda 3D Printer V1
* **Firmware Base:** Marlin `bugfix-2.1.x`
* **Mainboard:** BigTreeTech SKR Mini E3 V3
* **Motion System:** Cartesian
* **Drivers:** TMC2209 in UART mode
* **Power Supply:** 24V DC
* **Hotend:** All-metal (ceramic-compatible)
* **Supported Filament:** PLA, PET-G, Recycled PET

---

## 📦 Available Firmware Configurations

Xunda 3D supports two official firmware configurations based on the type of bed-leveling sensor installed:

### 🔹 BLTouch Configuration

* Bed Leveling: BLTouch (5-wire) sensor
* Dynamic Z-offset adjustment via LCD
* Enabled directive: `#define BLTOUCH`
* Probing Grid: 3x3 points
* Includes mesh validation routines

### 🔹 Inductive Probe Configuration

* Bed Leveling: Inductive (3-wire, NPN type)
* Fixed probe offsets set in firmware
* Requires a metallic print bed
* Slightly reduced probing coverage

---

## 📁 File Structure

```
Xunda3D-Marlin/
├── Marlin/
│   ├── Configuration.h                  ← default: BLTouch
│   ├── Configuration_adv.h
│
├── Xunda3D-Mods/
│   ├── README.md                        ← You're here
│   ├── ChangeLog.md                     ← Optional log of config changes
│   ├── BLTouch/
│   │   ├── Configuration.h
│   │   └── Configuration_adv.h
│   ├── InductiveProbe/
│   │   ├── Configuration.h
│   │   └── Configuration_adv.h
```

> 🔁 To switch configurations: replace `Configuration.h` and `Configuration_adv.h` in `/Marlin/` with the matching files from `BLTouch/` or `InductiveProbe/`.

---

## 🔧 Build & Flash Instructions

1. Open the firmware directory in **VS Code** using the **PlatformIO** extension.
2. Select the appropriate build environment in `platformio.ini`:

   ```ini
   [env:STM32F103RC_btt]
   ```
3. Compile and upload firmware to the printer via USB.

---

## ✅ Testing Checklist

- [x] X, Y, Z axis homing completes successfully  
- [x] Probe (BLTouch or Inductive) deploys and triggers properly  
- [x] Z-offset can be adjusted and stored  
- [x] Mesh bed leveling completes without error  
- [x] Endstops register correctly in firmware  
- [x] Thermistors report accurate temperatures  
- [x] Hotend and heated bed reach and hold target temps  
- [x] Stepper drivers operate quietly in StealthChop  
- [x] Test prints complete successfully using recycled PET filament  


---

## 👨‍💻 Maintainers

* Maintained by: XundaTech&#x20;
* Support Contact: [techxunda@gmail.com](mailto:techxunda@gmail.com)

---

## 🌍 About XundaTech

**XundaTech** is a Ugandan-based manufacturer of affordable 3D printers and recycled PET filament. Our mission is to democratize access to digital fabrication tools by building reliable, low-cost, and open-source printers tailored for schools and innovators across Africa.
