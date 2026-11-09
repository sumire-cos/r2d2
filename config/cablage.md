# Electrical Wiring

## 1. Overview

This document describes the current electrical connections of the R2-D2 robot.

It focuses on the Raspberry Pi 4, the L298N motor driver and the two track motors currently used for locomotion.

Only verified connections are documented as operational. Planned hardware integrations are identified separately.

## 2. Main Controller

**Controller:** Raspberry Pi 4 Model B Rev 1.5

The Raspberry Pi acts as the main computer of the robot. It sends control signals to the motor driver through its GPIO pins.

The Raspberry Pi and the motor power supply must share a common ground.

## 3. Motor Driver

**Driver:** L298N dual H-bridge motor driver

The L298N controls the two DC motors used for the robot's tracks.

### 3.1 GPIO Pin Assignment

| L298N Signal | Raspberry Pi GPIO | Function |
|---|---:|---|
| IN1 | GPIO 17 | Motor A direction |
| IN2 | GPIO 27 | Motor A direction |
| IN3 | GPIO 22 | Motor B direction |
| IN4 | GPIO 23 | Motor B direction |
| ENA | GPIO 12 | Motor A speed control (PWM) |
| ENB | GPIO 13 | Motor B speed control (PWM) |

**Important:** The ENA and ENB jumpers are removed to allow speed control through PWM signals from the Raspberry Pi.

The left/right track assignment must be confirmed against the actual motor output connections.

### 3.2 Motor Connections

The L298N provides two motor output channels:

- OUT1 / OUT2: Motor A
- OUT3 / OUT4: Motor B

Each channel controls one track motor.

**Motor model:** Mercury Motor MG37520E.

## 4. Power Supply

The current motor setup uses a 12 V battery to supply the L298N motor power input.

The Raspberry Pi and the motor driver share a common electrical ground.

### 4.1 Observed Voltage Measurements

The following measurements were recorded during testing:

| Measurement | Voltage |
|---|---:|
| Battery, measured separately | 11.99 V |
| L298N input | Approximately 10 V |
| Motor voltage without load | Approximately 9 V |
| Motor voltage under load | Approximately 6 V |

These measurements indicate a significant voltage drop under load.

The motor power supply and driver performance therefore require further investigation.

## 5. Audio Hardware

The robot currently uses a HiFiBerry DAC connected to the Raspberry Pi.

The following GPIO pins are reserved for the audio hardware:

- GPIO 18
- GPIO 19
- GPIO 21

These pins must not be reassigned without checking compatibility with the audio interface.

## 6. Current Hardware Status

| Component | Status |
|---|---|
| Raspberry Pi 4 | Operational |
| L298N motor driver | Connected |
| Left and right track motors | Connected |
| HiFiBerry DAC | Operational |
| Dome motor | Not connected |
| ESP32 dome controller | Planned |

## 7. Electrical Safety Notes

- Always disconnect the power supply before modifying wiring.
- Ensure that the Raspberry Pi and motor driver share a common ground.
- Do not connect the 12 V motor supply directly to Raspberry Pi GPIO pins.
- Check the polarity of power connections before switching on the system.
- Verify motor driver temperatures and supply voltage during load tests.
- Check the current requirements of each component before selecting a power supply.

## 8. Future Updates

This document should be updated whenever:

- A new component is connected.
- A GPIO assignment changes.
- The power distribution architecture is modified.
- A new controller or motor driver is integrated.
- A wiring configuration has been tested and validated.

Only verified electrical connections should be documented as operational.
