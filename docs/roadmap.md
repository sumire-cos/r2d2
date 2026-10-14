# Development Roadmap

## Overview

This roadmap tracks the development of the R2-D2-inspired robot, from hardware preparation to subsystem integration and functional validation.

Tasks will be updated as work progresses. A feature will only be marked as complete once it has been implemented and tested.

## Phase 1 — Hardware Inspection and Improvements

**Status: In progress**

- [ ] Inspect the existing robot structure and hardware
- [ ] Identify components requiring repair or improvement
- [ ] Perform the necessary repairs
- [ ] Validate the reliability of the existing hardware

## Phase 2 — Dome Mechanism Integration

**Status: In progress**

- [ ] Identify and document the mechanisms to be integrated
- [ ] Complete mechanical integration
- [ ] Define the control responsibilities of the ESP32
- [ ] Test each mechanism individually
- [ ] Validate safe and repeatable operation

## Phase 3 — Controller Communication

**Status: Planned / under development**

- [ ] Define the communication requirements between the Raspberry Pi and ESP32
- [ ] Select and document the communication method
- [ ] Define a message format for commands and status information
- [ ] Implement communication handling
- [ ] Test command delivery and error handling

## Phase 4 — Basic Locomotion

**Status: In development**

- [ ] Verify the drive hardware and motor connections
- [ ] Implement basic movement control
- [ ] Test individual movement commands
- [ ] Validate repeatable movement and stopping behaviour
- [ ] Document the limitations and results of the tests

## Phase 5 — Subsystem Integration

**Status: Planned**

- [ ] Integrate the validated subsystems
- [ ] Coordinate the Raspberry Pi and ESP32 responsibilities
- [ ] Test interactions between locomotion and dome mechanisms
- [ ] Investigate and resolve integration issues
- [ ] Document the validated system behaviour

## Phase 6 — Future Features

**Status: To be defined**

Potential future developments will be selected according to project priorities and hardware capabilities.

Each new feature will receive its own requirements, implementation tasks and validation criteria.

## Progress Tracking

The roadmap is a living document. Tasks and phase statuses will be updated when the project reaches new milestones.

A completed task means that its expected result has been verified, not merely that implementation has started.
