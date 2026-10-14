# R2-D2 — Personal Robotics Project

A personal robotics project focused on building, integrating and programming a custom R2-D2-inspired robot.

The project combines mechanical design, embedded systems, motor control and software development to progressively bring the robot to life.

## Project Overview

The robot has an existing physical structure. Current work focuses on repairing and improving selected components, integrating additional mechanisms, and developing the software required to control the robot.

Basic locomotion is a current development objective.

## System Architecture

The planned architecture separates high-level control from dedicated mechanism control.

- **Raspberry Pi 4:** Main computing unit responsible for coordinating robot functions and sending commands to the subsystems.
- **ESP32:** Dedicated controller for dome mechanisms, receiving commands from the Raspberry Pi.
- **Motor control:** Hardware and software responsible for basic locomotion.
- **Communication:** Wireless communication between the Raspberry Pi and ESP32 is being evaluated and developed.

The exact communication protocol and subsystem interfaces will be documented as implementation progresses.

## Development Status

- [x] Physical robot structure assembled
- [ ] Repair and improve selected components
- [ ] Integrate dome mechanisms
- [ ] Establish communication between the main controller and the ESP32
- [ ] Develop and validate basic locomotion
- [ ] Integrate and test the robot's subsystems

## Technical Areas

- Robotics and embedded systems
- Raspberry Pi and Linux
- ESP32 and microcontrollers
- Motor control and mechanism integration
- Wireless communication
- Software development and system integration

## Repository Structure

Documentation and technical resources will be organized as the project evolves.

- `docs/` — Architecture, technical documentation and development roadmap
- `media/` — Project photographs, diagrams and visual references

## Project Roadmap

The immediate priority is to improve the existing hardware, integrate the dome mechanisms and establish reliable control of the robot's basic movements.

Further development will depend on hardware validation and the integration of the different subsystems.

## Project Status

**Active development — hardware integration and software development in progress.**

This repository will be updated progressively as the project advances.
