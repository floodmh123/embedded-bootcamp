# Embedded Motor Tester

A low-level embedded systems project built on STM32 microcontrollers that reads analog potentiometer input through an external SPI ADC and converts it into PWM motor control signals.

This project was completed as part of an embedded firmware onboarding bootcamp focused on hardware-software integration, peripheral configuration, and real-time motor control.

---

# Overview

The system reads a potentiometer voltage (0V–3.3V) using an external MCP3004 Analog-to-Digital Converter (ADC) communicating over SPI.

The STM32 MCU processes the ADC data and generates a PWM signal to control a motor or servo.

This project demonstrates:

- Embedded firmware development
- SPI communication
- Timer/PWM configuration
- STM32 peripheral setup
- Hardware-software interaction
- Low-level debugging

---

# Features

## SPI-Based ADC Communication

- Configured STM32 SPI peripheral in Full-Duplex Master mode
- Communicated with MCP3004 external ADC chip
- Implemented chip-select (CS) control using GPIO
- Read 10-bit analog input values over SPI

## PWM Motor Control

- Generated 50Hz PWM signal using STM32 timers
- Produced 1ms–2ms pulse widths for motor/servo control
- Dynamically adjusted duty cycle based on potentiometer input

## Embedded Peripheral Configuration

- Configured MCU peripherals using STM32CubeIDE and CubeMX
- Set up GPIO, SPI, and TIM peripherals from hardware schematics
- Generated HAL initialization code using `.ioc` configuration

## Low-Level Firmware Development

- Used STM32 HAL drivers for hardware abstraction
- Implemented ADC-to-PWM conversion logic
- Debugged firmware and compiler issues directly on embedded hardware

---

# Hardware Components

- STM32 Nucleo-F072RB
- MCP3004 SPI ADC
- Potentiometer
- Servo / Motor
- STM32CubeIDE

---

# Pin Configuration

| MCU Pin | Function |
|---|---|
| PB8 | SPI Chip Select |
| PB3 | SPI Clock (SPI1_SCK) |
| PA6 | SPI MISO |
| PA7 | SPI MOSI |
| PA8 | PWM Output (TIM1_CH1) |

---

# System Workflow

```text
Potentiometer
      ↓
External ADC (MCP3004)
      ↓  SPI
STM32 MCU
      ↓
PWM Signal Generation
      ↓
Motor / Servo Control
```

---

# PWM Behavior

The firmware converts the ADC reading into a PWM duty cycle:

- Frequency: `50Hz`
- Pulse Width:
  - `1ms` → minimum position/speed
  - `2ms` → maximum position/speed

This signal format is commonly used for:

- Servo motors
- ESC motor controllers
- Motor testing rigs

---

# Technologies Used

- C
- STM32 HAL
- STM32CubeIDE
- SPI Communication
- PWM / Timer Peripherals
- Embedded Systems
- Real-Time Hardware Control

---

# Project Goals

This project was designed to strengthen understanding of:

- Embedded firmware architecture
- Hardware peripheral configuration
- MCU timer systems
- Serial communication protocols
- Real-world debugging workflows
- Hardware/software integration

---

# Future Improvements

Potential extensions include:

- DMA-based SPI communication
- Interrupt-driven ADC sampling
- OLED debug display
- Multi-channel ADC support
- PID motor control
- RTOS integration
- Wireless telemetry

---

# Repository

[embedded-bootcamp](https://github.com/floodmh123/embedded-bootcamp)
