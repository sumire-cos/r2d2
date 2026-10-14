# System Architecture

## 1. Overview

The R2-D2 project uses a distributed control architecture. A main computing unit coordinates the robot, while a dedicated microcontroller manages specific mechanisms.

The architecture is designed to separate high-level coordination from low-level hardware control.

## 2. Main Components

### 2.1 Raspberry Pi 4 — Main Controller

The Raspberry Pi 4 acts as the robot's main computing unit.

Its planned responsibilities include:

- Coordinating the robot's subsystems
- Processing high-level commands
- Sending control instructions to dedicated controllers
- Managing software responsible for overall robot behaviour
- Providing a foundation for future features

### 2.2 ESP32 — Dome Mechanism Controller

The ESP32 is dedicated to the mechanisms installed in the robot's dome.

Its planned responsibilities include:

- Receiving commands from the Raspberry Pi
- Controlling the dome's mechanisms
- Managing low-level operations assigned to the microcontroller
- Reporting relevant status information when the communication interface supports it

The exact responsibilities will be refined as the mechanisms are integrated.

### 2.3 Locomotion System

The locomotion system provides the robot's basic movement.

Its development includes:

- Integrating and checking the drive hardware
- Developing the control software
- Testing movement commands
- Validating reliable operation before adding more advanced behaviour

The final control interfaces and division of responsibilities remain to be documented.

## 3. Communication

Wireless communication between the Raspberry Pi and the ESP32 is being considered for exchanging commands and, where required, status information.

The communication method, protocol, message format and error-handling strategy will be documented once they have been selected and validated.

## 4. Control Principles

The intended design follows these principles:

- **Separation of responsibilities:** each controller has a defined role.
- **Modularity:** subsystems should be developed and tested independently where practical.
- **Reliability:** communication and movement must be validated before more complex features are added.
- **Maintainability:** technical decisions and interfaces should be documented as the project evolves.

## 5. Current Status

The physical structure of the robot is assembled. Selected components are being repaired or improved, additional mechanisms are being integrated, and software development is in progress.

Basic locomotion remains a development objective.

## 6. Future Documentation

This document will be expanded as the design is validated, including:

- A detailed subsystem diagram
- Hardware interfaces and connections
- Communication protocol
- Control responsibilities
- Failure handling and recovery behaviour
