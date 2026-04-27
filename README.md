# ADC Validation Platform
*A modular testbed for evaluating analog signal chains in motor control applications*

---
## ⚠️ Development Status
> **Work in Progress**: This repository is actively developed as part of my **Master’s project** at HTWG Konstanz. The current README is a draft and will be expanded with hardware designs, firmware, and validation results.

---

## 📌 Overview
This repository provides **design files, firmware, and validation tools** for a custom **ADC validation board**, developed as an extension to my **Bachelor’s thesis** on the ["DIY Power PCB"](link-to-pdf) (HTWG Konstanz, 2024). While the original thesis used the **ESP32’s internal ADC** (limited by nonlinearity and noise), this platform focuses on:

### **Core Objectives**
1. **External ADC Validation**:
   - Replace the ESP32’s internal ADC with a **MCP3208/MCP3008** (12-bit, 8-channel) to quantify improvements in **noise floor, linearity, and temperature stability** for current measurements.
   - *Key question*: Does an external ADC justify the added complexity/cost in motor control applications?

2. **Full Analog Chain Analysis**:
   - Evaluate the **entire signal path**:
     - **Shunt-based current sensing** (bridge currents)
     - **Operational amplifiers** (e.g., [OPV model]) for signal conditioning
     - **High-end current sensors** (e.g., [ACS71231, INA240]) as alternatives to shunts
   - *Goal*: Identify the **weakest link** in the chain (ADC vs. sensors vs. OPVs) and optimize cost/performance trade-offs.

3. **BLDC Motor Control Context**:
   - Target application: **Precise phase current measurement** for FOC (Field-Oriented Control) of BLDC motors.
   - Compare budget vs. high-end components to determine **where to invest** for maximum accuracy.

---

## 🔗 Related Work
- **Bachelor’s Thesis**: ["DIY Power PCB" (PDF, German)](link-to-pdf) – Foundation for this project, focusing on the ESP32-based power distribution board.
- **Master’s Project**: Extends the thesis by adding **modular ADC validation** and analog chain analysis.

---

## 🛠️ Features

- **Hardware:**
  - [ADC Model] with [resolution]-bit resolution
  - [MCU Model, e.g., STM32F4] for data acquisition
  - Low-noise power supply and signal conditioning
- **Firmware:**
  - Written in **C/C++** using [ESP-IDF/PlatformIO/Arduino]
  - Supports **I2C/SPI communication** and **PWM calibration**
- **Validation:**
  - Automated test scripts (Python)
  - Noise floor analysis and linearity plots

---

## 📂 Repository Structure

```
adc-validation-board/
├── hardware/          # KiCad schematics, PCB layouts, BOM
├── firmware/          # Source code for MCU
├── software/          # Test scripts (Python/MATLAB)
├── docs/              # Datasheets, thesis excerpts, results
└── images/            # Photos, plots, diagrams
```

---

## 🚀 Getting Started

### Prerequisites

- **Hardware:** [List components, e.g., ADC chip, MCU, power supply]
- **Software:**
  - [KiCad](https://www.kicad.org/) for PCB design
  - [PlatformIO](https://platformio.org/) for firmware development
  - Python 3.8+ for test scripts

### Installation

1. Clone the repository:
  ```bash
   git clone https://github.com/your-username/adc-validation-board.git
  ```
2. Open the firmware in [your IDE] and flash it to the MCU.
3. Run validation tests:
  ```bash
   cd software/tests
   python3 noise_analysis.py
  ```

---

## 📊 Validation Results

Key findings from the thesis:

- **Noise floor:** [X] µV RMS @ [sampling rate]
- **INL/DNL:** [Y] LSB (see [plot](#))
- **Temperature drift:** [Z] ppm/°C

*Example: Noise spectrum of the ADC at 1 kSPS*

🔗 **[Full results in the thesis](#)**

---

## 🎓 Thesis Summary

### Abstract

[2–3 sentences summarizing your thesis goals, e.g.:  
*"This work evaluates the suitability of the [ADC Model] for precision applications in embedded systems. A custom validation board was designed to measure noise, linearity, and temperature effects, achieving [key result] under [conditions]."*)

### Key Contributions

- Designed and assembled a **low-noise ADC validation platform**.
- Developed **firmware for automated calibration** and data logging.
- Validated performance against **industry standards** (e.g., [reference]).

📄 **[Download the full thesis (PDF)](link-to-pdf)**

---

## 🔧 Built With

- **Hardware:** KiCad, [ADC Model], [MCU Model]
- **Firmware:** C/C++, [ESP-IDF/PlatformIO]
- **Analysis:** Python (NumPy, Matplotlib), [MATLAB/Octave]

---

## 🤝 Contributing

Contributions are welcome! Open an issue or submit a pull request for:

- Bug fixes
- Additional test cases
- Documentation improvements

---

## 📜 License

This project is licensed under the **MIT License** – see [LICENSE](LICENSE) for details.

---

## 📬 Contact

Fabian Zaske – [your.email@example.com](mailto:your.email@example.com)  
🔗 [Portfolio/Website](your-portfolio-link) | [LinkedIn](your-linkedin)

---

*"Precision matters – in bits and in life."*
