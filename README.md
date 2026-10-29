# Boost Converter Controller using Arduino & MATLAB (Advanced Serial Communication)

[![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D?style=for-the-badge&logo=arduino&logoColor=white)](https://www.arduino.cc/)
[![MATLAB](https://img.shields.io/badge/MATLAB-R2019b%2B-e16727?style=for-the-badge&logo=mathworks&logoColor=white)](https://www.mathworks.com/products/matlab.html)
[![Simulink](https://img.shields.io/badge/Simulink-Simulation-0076A8?style=for-the-badge&logo=mathworks&logoColor=white)](https://www.mathworks.com/products/simulink.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

An end-to-end hardware-in-the-loop (HIL) closed-loop power electronics control system for a DC-DC Boost Converter using an **Arduino Uno** micro-controller and **MATLAB/Simulink** interface over fast serial communication.

This project features high-frequency PWM switching, embedded digital PI closed-loop voltage regulation, real-time MATLAB data streaming/plotting, and an **Automated PID Parameter Auto-Tuning Script**.

---

## 📽️ Tutorial & Demo Video

Watch the step-by-step setup, hardware testing, and MATLAB serial integration on YouTube:

[![Boost Converter Project Video](https://img.youtube.com/vi/u_BvbkpHOao/hqdefault.jpg)](https://www.youtube.com/watch?v=u_BvbkpHOao)

👉 **[Click Here to Watch the Video Demonstration](https://www.youtube.com/watch?v=u_BvbkpHOao)**

---

## ✨ Key Features

* **⚡ Fast Embedded Control Loop (1 ms):** The Arduino firmware executes a fast digital PI control loop every 1 ms, updating PWM duty cycle values to stabilize target voltage.
* **📡 Non-Blocking Serial Telemetry (50 ms):** Transmits voltage feedback ($V_{out}$) and duty cycle parameters without delaying the high-frequency switching cycle.
* **💻 Interactive MATLAB Controller GUI Script (`boostIO.m`):** Adjust reference target voltage ($V_{ref}$), proportional gain ($K_p$), and integral gain ($K_i$) dynamically from MATLAB while live-plotting voltage responses.
* **🤖 Automated PI Parameter Tuning (`analyze_steps.m`):** Runs sequential step-response experiments to evaluate cost functions ($J$) and select optimal gains automatically.
* **🛡️ Hard-Coded Over-Voltage Protection (OVP):** Built-in micro-controller safety limits automatically cut off MOSFET drive if output voltage exceeds unsafe thresholds.
* **📐 MATLAB / Simulink Simulation (`boost_simulink.slx`):** Included simulation model to test control laws before deployment on real hardware.

---

## 🛠️ Hardware Requirements & Pinout

| Component | Specification / Value | Arduino Pin | Notes |
| :--- | :--- | :--- | :--- |
| **Microcontroller** | Arduino Uno / Nano | - | Standard ATmega328P board |
| **Switching Transistor** | N-Channel MOSFET (e.g., LR7843 / IRFZ44N) | **PWM Pin 9** | High-frequency gate control |
| **Voltage Sensing** | Voltage Divider Network ($R_1 = 40\text{ k}\Omega$, $R_2 = 10\text{ k}\Omega$) | **Analog Pin A5** | Scales 0–25V down to 0–5V |
| **Inductor** | 100 µH – 220 µH | Circuit | High current rating rating |
| **Diode** | Schottky Fast Recovery (e.g., 1N5819 / SS34) | Circuit | Output rectification |
| **Filter Capacitor** | 100 µF – 470 µF (25V+) | Circuit | Output smoothing |

---

## 📂 Project Repository Structure

```
boost_controller_using_arduino_matlab_serial_adnavce_communication/
│
├── boost_controller_using_arduino_matlab/
│   └── boost_controller_using_arduino_matlab.ino  # Embedded PI firmware for Arduino
├── boostIO.m                                       # Interactive MATLAB live controller & scope
├── analyze_steps.m                                 # Auto-tuning & cost-function evaluation script
├── build_boost_model.m                             # Programmatic script to build Simulink model
├── boost_simulink.slx                              # MATLAB Simulink model file
├── Command Note.txt                                # Quick terminal commands and notes
└── README.md                                       # Project documentation
```

---

## 🚀 Quick Start & Installation

### 1. Arduino Setup
1. Open `boost_controller_using_arduino_matlab.ino` in the **Arduino IDE**.
2. Select your **Arduino Board** and **COM Port**.
3. Upload the code to your Arduino.
4. Verify hardware connections according to the circuit pinout table.

### 2. MATLAB Control & Live Telemetry
1. Open MATLAB (R2019b or newer recommended).
2. Set the working directory to the project repository folder.
3. Open and run `boostIO.m`.
4. Select your Serial Port (e.g., `'COM3'`) and set the baud rate to **115200**.
5. Adjust target output voltage ($V_{ref}$) and tune $K_p$/$K_i$ parameters in real-time.

### 3. Running Auto-Tuning Analysis
1. Open `analyze_steps.m` in MATLAB.
2. Run the script to execute automatic step testing and performance calculation.

---

## ⚙️ Control & Serial Protocol Format

Telemetry data streamed from Arduino to MATLAB follows a structured CSV line format:
```text
Vout:12.45,Duty:42.5
```
Commands sent from MATLAB to Arduino:
```text
SET:Vref=12.00,Kp=0.45,Ki=0.08
```

---

## 🤝 Contributing & Support

Contributions, issues, and feature requests are welcome!  
Feel free to open an issue or pull request on the [GitHub Issues](https://github.com/rkrazowan/boost_controller_using_arduino_matlab_serial_adnavce_communication/issues) page.

---

## 📜 License

This project is licensed under the **MIT License**.
