Universal Interface Multi-Tool (UI/MT)

*A handheld “sci-fi” diagnostic, communication, and signal-emulation device — designed for real engineering use.*

---

##  Overview

**UI/MT (Universal Interface Multi-Tool)** is a multifunction handheld system built around the **ESP32-WROOM-DA** and a **320×240 TFT touch display**.
It’s designed to feel like a **video-game gadget come to life** — a “hacking-style” interface that’s fun, immersive, and satisfying — but also fully functional, safe, and legally compliant for real engineering, prototyping, and educational use.

UI/MT acts as a **scanner, analyzer, configurator, and signal generator**, allowing users to communicate with, test, and interact with electronic systems and networks through a unified, tactile, and engaging interface.

---

##  Project Goals

* Create a **universal interface platform** that can communicate, scan, analyze, and command devices over multiple mediums (wired + wireless).
* Provide a **functional engineering tool** that doubles as a **learning and exploration device**.
* Deliver a **rich UI/UX experience** inspired by sci-fi and video-game interfaces — smooth, responsive, and intuitive.
* Maintain **legality and safety** — no malicious or disallowed transmission capabilities.
* Modular architecture — new modules and hardware extensions can be added later.

---

##  Core Capabilities

| Category                                 | Description                                                                                              |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Wireless Scanner**                     | Wi-Fi and BLE analyzer; lists devices, RSSI, channels, encryption; exportable logs.                      |
| **Serial & Bus Console**                 | UART, I²C, and SPI bridge and injector; monitor, send commands, and log communication.                   |
| **Signal Emulator / Function Generator** | Generate sine, square, triangle, saw, PWM, and modulated waveforms via DAC, PWM, or DDS (AD9833/AD9850). |
| **IR & RF Transmitter (Dev Mode)**       | Transmit or replay low-power IR/RF sequences; NEC/RC5 templates; safety-locked behind Dev Mode.          |
| **Logic Mini-Analyzer**                  | Capture and visualize digital transitions; simple UART or pulse decoding.                                |
| **Storage & Scripting**                  | SD-based JSON presets, macros, and logs; timestamped with RTC/NTP clock.                                 |
| **UI System**                            | Multi-mode touch interface with swipe navigation, quick actions, and always-visible status bar.          |
| **Security / Dev Mode**                  | TX lock, safety confirmation dialogs, automatic logging of all transmissions.                            |

---

##  Extended Utilities (Other Functions)

---

##  How the Tab Works

* Each utility runs as a **standalone app** within the “Other Functions” shell.
* The bottom bar shows `[◀ Prev] [Home] [Next ▶]`.
* Utilities can be launched via search or favorites.
* Preferences (e.g., units, color mode, 12/24 h clock) saved in `/config/settings.json`.

---

##  Summary

The **Other Functions** section turns the UI/MT from a tool into an *ecosystem*.
It complements the main scanning and signal tools with everything an engineer, technician, or student might need on the go — calculators, conversions, education, and reference material — all wrapped in the same smooth, immersive interface.

---

##  UI / UX Design Philosophy

UI/MT’s interface merges **practicality** with **immersive design**.
Every action feels intentional, animated, and responsive — like using a sci-fi in-game scanner, but for real engineering tasks.

### Core UI Features

* **Always-on status bar** → Battery, Wi-Fi, BLE, SD, DevMode, and Clock
* **Mode carousel** → Swipe or encoder to switch between modes
* **Quick-action HUD** → One-tap shortcuts for SCAN / EMULATE / CONNECT
* **Radial command wheel** → Long-press center to jump between tools
* **Context-sensitive menus** → Change dynamically by mode
* **Simulation mode** → Visualize results without output for safe testing
* **Theming system** → Dark neon palette with accent highlights

### Visual & Audio Aesthetic

| Element    | Style                                                           |
| ---------- | --------------------------------------------------------------- |
| Palette    | Dark base (#101018) + Neon accents (Cyan, Lime, Amber)          |
| Font       | Orbitron / Audiowide (sci-fi HUD aesthetic)                     |
| Animations | Smooth ease-in/out transitions, radar sweeps, waveform previews |
| Sound      | Soft “ping” (confirm), “thud” (error), “sweep” (scan active)    |

---

##  Modes & Menus

### 1. **Home HUD**

Central radar-style interface showing device status and quick actions.

* Radar sweep animation with signal blips
* Buttons: `[SCAN] [EMULATE] [CONNECT]`
* Long-press → Quick command wheel

### 2. **Scanner**

Displays Wi-Fi and BLE devices with real-time RSSI bars and channel histograms.

* “Start/Stop” scan button
* Export results to SD as CSV/JSON

### 3. **Console**

Multi-bus serial terminal for UART, I²C, and SPI.

* Scrollable hex/text view
* Baud/address/mode settings
* Macros and injection tools
* Color-coded TX/RX

### 4. **Signal Emulator (Function Generator)**

Full signal generation suite with waveform preview.

* Waveforms: sine, square, triangle, saw, PWM, sweep
* Outputs: DAC, PWM, or DDS (AD9833/AD9850)
* Parameters: freq, amplitude, duration, attenuation
* Presets & logging
* Safety confirmation before TX

### 5. **IR / RF Transmit (Dev Mode)**

* Predefined & learned signals (IR NEC/RC5)
* RF OOK/ASK templates (CC1101/SI4463)
* Locked by default (TX disabled until user enables Dev Mode)

### 6. **Scripting & Macros**

* Create or run macros combining GPIO, UART, delays, reads, and writes
* Run in simulation or active mode
* Save as JSON for reuse

### 7. **Diagnostics & Configurator**

* Touch, SD, RTC, Wi-Fi/BLE self-tests
* I²C bus scan
* ADC test, LED blink, calibration, firmware info

### 8. **Data / Storage Center**

* Explore SD contents (logs, presets, macros)
* View, export, delete

### 9. **Security / Dev Mode**

* Toggles for IR/RF TX, UART inject, I²C write
* Safety & legal reminders before unlocking

### 10. **Other Functions**

* Utility and educational tools (calculators, guides, tutorials, etc.)

*Utility and educational tools that complement the main engineering features — designed for convenience, quick reference, and learning.*

The **Other Functions** tab acts as your “utility bay” — accessible from the mode carousel or radial menu. It contains a series of lightweight, instantly available tools that make UI/MT a complete pocket companion for lab work, debugging, and learning.

Each utility launches in its own **touch-friendly tile interface**, with consistent navigation:

* Swipe left/right → change utility
* Tap “Home” icon → return to HUD
* Tap top-right clock → view Time Settings

---

####  1. Real-Time Clock & Status

**Purpose:** Provide accurate timekeeping and synchronization for logs, timestamps, and user convenience.

**Features:**

* Always-visible digital clock overlay (top-right, every screen)
* Syncs with NTP over Wi-Fi; automatic RTC update (DS3231)
* Manual time/date set option
* 12/24-hour toggle
* Last-sync indicator (green dot = synced)
* Stored timezone offset
* Backup power monitoring for RTC

**Interface:**

```
[15:42:19]  UTC-7  |  Source: NTP
Last Sync: 15:41:00 (Success)
[Sync Now]  [Manual Set]  [12/24h Toggle]
```

---

####  2. Electrical Calculator Suite

**Purpose:** Quick calculations for electronics design and troubleshooting.

**Included Calculators:**

| Name                      | Formula                         | Description                                |
| ------------------------- | ------------------------------- | ------------------------------------------ |
| **Ohm’s Law**             | V = I × R                       | Compute voltage, current, or resistance.   |
| **Power Law**             | P = V × I                       | Calculate electrical power.                |
| **Voltage Divider**       | Vout = Vin × (R2 / (R1 + R2))   | For level shifting and bias circuits.      |
| **RC Time Constant**      | τ = R × C                       | Charge/discharge timing analysis.          |
| **Reactance (C/L)**       | Xc = 1/(2πfC), Xl = 2πfL        | Impedance components for AC circuits.      |
| **Resistor Code Decoder** | Color bands ↔ Value ↔ Tolerance | Visual helper for resistor identification. |

**Features:**

* Live update as you type
* SI prefix recognition (µ, m, k, M)
* Auto E12/E24 rounding
* Copy result to clipboard
* Save as JSON preset

**UI Example:**

```
Ohm’s Law
[ V=____ ]  [ I=____ ]  [ R=____ ]
[Calculate]   Result:  I = 12.5 mA
```

---

####  3. Unit & Base Converter

**Purpose:** Simplify unit conversions commonly used in electronics and computing.

**Categories:**

* Decimal ↔ Binary ↔ Hexadecimal
* Frequency ↔ Period
* dB ↔ Linear Power Ratio
* Temperature (°C ↔ °F ↔ K)
* Voltage (mV ↔ V ↔ kV)
* Resistance / Capacitance / Inductance scaling

**Example:**

```
Input: 10 kHz
Output: 0.1 ms
```

**Extras:** copy results, auto unit prefix handling, and color-coded results for readability.

---

####  4. Reference Guides (Educational)

**Purpose:** Quick access to compact educational guides explaining protocols, components, and standards.

**Sections:**

| Guide                   | Summary                                                    |
| ----------------------- | ---------------------------------------------------------- |
| **UART**                | Frames, baud rates, voltage levels, parity, stop bits.     |
| **I²C**                 | Addressing, pull-ups, start/stop sequence, timing diagram. |
| **SPI**                 | Modes 0–3, CPOL/CPHA, clock polarity, daisy-chaining.      |
| **BLE / Wi-Fi**         | Advertising, RSSI, channels, MAC addressing basics.        |
| **IR Communication**    | NEC, RC5 format basics, safe TX limits.                    |
| **PCB & Wiring Basics** | Ground loops, signal integrity, decoupling.                |

**Display:** Scrollable pages with diagrams and minimal text (offline Markdown rendered to TFT).
**Goal:** Help users understand what the console or scanner is showing.

---

####  5. Cheat-Sheets

**Purpose:** On-device quick lookup tables and charts for everyday work.

**Sheets include:**

* **Resistor color code** chart
* **Common baud rates** (9600–115200–921600)
* **Logic voltage levels** (3.3 V ↔ 5 V safe ranges)
* **Connector pinouts:** UART, I²C, SPI, USB, JST
* **GPIO reference:** ESP32 pin capabilities (ADC/DAC/PWM)

**Display:** Swipeable cards; tap to expand to full page.

---

####  6. Tone Generator

**Purpose:** Quick audio or PWM signal generation for simple testing.

**Outputs:**

* DAC (GPIO25 or 26) → Sine tone
* PWM (GPIO16 or similar) → Square tone

**Features:**

* Adjustable frequency (1 Hz – 10 kHz)
* Adjustable duration and amplitude
* Simple sweep mode
* Use for buzzer, speaker, or input testing

**UI Example:**

```
Freq: [1.0 kHz]   Amplitude: [0.5 Vpp]
[PLAY] [STOP] [SWEEP ▾]
```

---

####  7. File Manager & Viewer

**Purpose:** Browse and manage SD card data.

**Features:**

* Navigate directories (`/logs`, `/macros`, `/presets`)
* View text/CSV/JSON files directly on-screen
* Delete, rename, or export over BLE/Wi-Fi
* File info: size, date modified, type icon

**UI Example:**

```
/SDCARD
 ├── ScanLogs/
 │    ├── log_2025_11_05.csv
 │    └── log_2025_11_04.csv
 ├── Macros/
 │    └── uart_bootseq.json
 └── Presets/
      └── sine_1khz.json
```

---

####  8. Network Tools (Passive)

**Purpose:** Non-invasive diagnostics and network awareness utilities.

**Tools:**

* Local IP info display (Wi-Fi connection details)
* DNS lookup (hostname ↔ IP)
* Ping test (safe, rate-limited)
* Signal strength meter (RSSI)

**Display:**

```
IP: 192.168.0.123
SSID: HomeLab
RSSI: -54 dBm
DNS Lookup: google.com → 142.250.68.14
[Ping Test] [Copy Info]
```

---

####  9. Macro Templates

**Purpose:** Provide ready-made script templates for automation.

**Examples:**

| Template                 | Description                           |
| ------------------------ | ------------------------------------- |
| **UART Bootloader Ping** | Send 0x55 every 100 ms; wait for ACK. |
| **I²C Sensor Read**      | Read register 0x0F; print value.      |
| **IR TV Toggle**         | Replay stored NEC pattern once.       |

**Actions:**

* “Load to Editor” → open in Scripting Engine
* “Run Simulation” → dry-run to verify logic
* “Save Copy” → modify and reuse

---

####  10. Tutorials & Help

**Purpose:** Interactive, guided lessons and responsible-use reminders.

**Tutorial Topics:**

* “How to Scan Wi-Fi & BLE safely”
* “Using UART Console without TX”
* “Reading I²C Devices”
* “Signal Generator Setup & Cautions”

**Help Section:**

* Explains Dev Mode safety
* Regional RF regulations summary
* UI/MT system architecture overview
* License & open-source credits

---

##  Hardware Architecture

| Component                               | Function                                         |
| --------------------------------------- | ------------------------------------------------ |
| **ESP32-WROOM-DA**                      | Dual-antenna MCU; Wi-Fi, BLE, and logic control. |
| **ILI9341 320×240 TFT Touch (XPT2046)** | UI display and user input.                       |
| **Micro-SD card**                       | Data storage, logs, and presets.                 |
| **RTC module (DS3231)**                 | Accurate timekeeping with NTP sync.              |
| **DAC / DDS module (MCP4921 / AD9833)** | Precision analog and waveform output.            |
| **Level shifters / isolation**          | Safe interfacing with 5 V systems.               |
| **Op-amp buffer / LPF**                 | Clean signal output and amplitude control.       |
| **Optional RF (CC1101 / SI4463)**       | Sub-GHz low-power transmissions (dev-locked).    |
| **Power / battery system**              | Li-ion + USB-C charging (planned).               |

---

##  Software Architecture

**Core modules**

```
/src
 ├─ drivers/     → TFT, touch, DAC, SPI, I²C, UART
 ├─ ui/          → screens, HUD, animations, themes
 ├─ signal/      → waveform generator, presets
 ├─ console/     → serial bridges, parsers
 ├─ scanner/     → Wi-Fi, BLE scanning, RSSI mapping
 ├─ scripts/     → macro interpreter
 ├─ utils/       → NTP, SD, RTC, config
 └─ security/    → dev lock, permissions
```

---

##  Safety & Legal Compliance

UI/MT is designed to **educate, analyze, and test safely** — not to interfere with real systems.
All transmission-capable features (IR/RF/UART inject) are **locked behind Dev Mode** and require explicit user consent.
Each TX event is **automatically logged** to SD with a timestamp.
The project encourages **ethical, responsible, and lawful experimentation** in accordance with regional RF and data regulations.

---

##  Typical Use Cases

| Use Case                     | Description                                                    |
| ---------------------------- | -------------------------------------------------------------- |
| **Wireless Network Mapping** | Analyze Wi-Fi/BLE signal strength in your lab.                 |
| **Embedded Debugging**       | Connect to UART or I²C devices for quick diagnostics.          |
| **Signal Testing**           | Output sine or square waves for circuit tuning or calibration. |
| **Educational Demos**        | Teach communication protocols interactively.                   |
| **Automation & Macros**      | Build small automated testing sequences.                       |
| **Field Diagnostics**        | Portable oscilloscope-lite and serial console.                 |

---

##  Why It’s Relevant

* Combines multiple bench instruments (multimeter, function generator, logic analyzer, serial terminal) into one compact handheld platform.
* Provides **visual, interactive feedback** for learners and professionals.
* Bridges **technical utility** with **creative, immersive UX** — making engineering engaging.
* Open-source architecture → expandable hardware and firmware.

---

##  Project Status

| Stage                        | Progress                           |
| ---------------------------- | ---------------------------------- |
| Hardware design              |  TFT + touch + SD + RTC confirmed |
| UI mock / UX test            |  functional (ESP32 + ILI9341)     |
| Core architecture            |  in development                  |
| Function generator (DAC/DDS) |  planned next                    |
| IR / RF TX integration       |  dev-mode stage                  |
| Full scripting engine        |  future milestone                |

---

##  License & Attribution

Open hardware / open software project under **MIT License**.
Created by **Victor Granado** — Computer Engineering, BYU-Idaho.
Inspiration drawn from *Flipper Zero*, *multimeters*, and *sci-fi interface design.*

---

##  Project Vision

> *“The UI/MT blurs the line between engineering instrument and game interface — making discovery, diagnostics, and electronics feel alive.”*
