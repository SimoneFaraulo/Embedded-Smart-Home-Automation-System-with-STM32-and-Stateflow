# Embedded-Smart-Home-Automation-System-with-STM32-and-Stateflow
---

## 📌 Overview

This project implements an **embedded system for smart home automation**.  
It controls multiple devices in a domestic environment, allowing:

- Automated **blinds angle regulation**
- **Lighting** control (manual or timed)
- **Heating** temperature regulation

The system was modeled using **Simulink Stateflow**, and the generated C code was integrated into a firmware project created with **STM32CubeMX** for an **STM32 Nucleo G474RE** board.

Interaction is provided via:

- **UART interface** for configuration and real-time monitoring  
- **Physical buttons** for direct manual control  
- **LED indicators** for visual system status feedback

---

## ⚙️ Features

- System activation and deactivation
- Configuration mode via UART
- Execution mode to operate devices using saved configuration
- Blinds control (0°–180° in steps of 20°)
- Lighting control (on/off or timed activation)
- Heating temperature control (16–30°C with RGB color feedback)
- Real-time status display on UART

---

## 🧠 Architecture

The system is designed as a **finite state machine** with the following main states:

- **InactiveSystem**  
- **ActiveSystem**
  - **ConfigurationDevice**
  - **ExecutionDevice**

The Simulink model manages state transitions and logic, while CubeMX provides the hardware abstraction for GPIO, UART, and PWM peripherals.

---

## 📁 Repository Structure

```
├── project/ # STM32CubeMX firmware project
├── simulink_model.slx # Simulink + Stateflow model (.slx)
├── README.md
└── report.pdf
```
---

## 🚀 Deployment and Operation

1. **Simulink Model Execution and Code Generation**
   - Open the Simulink model located at `simulink_model.slx`.
   - Perform a full simulation to verify system logic and state transitions.
   - Generate C code using **Embedded Coder**, ensuring proper configuration to integrate with the STM32CubeMX project in the `project/` directory.
   - Confirm that generated peripheral initialization and state machine code is correctly mapped to the STM32 hardware abstraction layer (HAL).

2. **Firmware Compilation and Flashing**
   - Open the STM32CubeMX project in STM32CubeIDE.
   - Import the generated C code into the project workspace.
   - Build the firmware and flash it to the **STM32 Nucleo G474RE** board via ST-Link.

3. **System Interaction**
   - Establish a UART connection at **115200 baud** for real-time monitoring and configuration.
   - Operate the system using:
     - **Physical buttons** for manual activation, device configuration, and lighting control.
     - **UART commands** to modify configuration parameters and query system status in real time.

## 📄 Documentation

A detailed description of the system, use cases, state diagrams, and implementation is provided in the report:

**`report.pdf`**

---

## 📜 License

This project was developed for educational purposes as part of the Embedded Systems course.  
Feel free to reuse and modify it with proper attribution.
