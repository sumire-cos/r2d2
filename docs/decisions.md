# Technical Decisions

## Purpose

This document records the main technical decisions made during the development of the R2-D2-inspired robot.

Each decision should explain the context, the chosen approach, the reasons behind it, and any consequences or limitations.

Decisions may be revised when testing or new requirements justify a change.

## Decision 001 — Separate Main Control from Mechanism Control

**Status:** Adopted

### Context

The robot requires a main computing unit to coordinate its behaviour and a dedicated controller for the dome mechanisms.

### Decision

The Raspberry Pi 4 is assigned the role of main controller, while the ESP32 is assigned responsibility for the dome mechanisms.

### Rationale

This separation establishes clear responsibilities between the main computer and the microcontroller. It also provides a modular foundation for developing and testing the subsystems independently.

### Consequences

- High-level coordination is handled by the Raspberry Pi.
- Dome mechanism control is assigned to the ESP32.
- Communication between the controllers must be defined and validated.
- The detailed interfaces and responsibilities may evolve as integration progresses.

## Decision 002 — Evaluate Wireless Communication Between Controllers

**Status:** Under evaluation

### Context

The Raspberry Pi and ESP32 need to exchange commands. Wireless communication is being considered for the connection between the two systems.

### Decision

The communication method will be selected after evaluating the project's requirements and testing the available options.

### Evaluation Criteria

- Reliability in the robot's operating environment
- Communication latency
- Connection stability
- Implementation complexity
- Recovery from communication loss
- Compatibility with the controllers and software

### Consequences

The communication method and protocol remain to be documented once a solution has been selected and validated.

## Decision 003 — Develop and Validate Subsystems Incrementally

**Status:** Adopted

### Context

The robot combines mechanical components, electronic controllers, locomotion and dome mechanisms.

### Decision

Subsystems will be developed and tested individually where practical before being integrated into the complete robot.

### Rationale

Incremental validation helps isolate faults, makes troubleshooting easier and reduces uncertainty during system integration.

### Consequences

- Individual components and mechanisms should be tested before full integration.
- Test results should be documented.
- Features should only be marked as complete after their expected behaviour has been verified.

## Future Decisions

Additional entries will document decisions concerning:

- Motor control architecture
- Controller communication protocol
- Power distribution and electrical protection
- Mechanism interfaces
- Software organization
- Error handling and recovery

New decisions should be added when a choice has a meaningful impact on the architecture, reliability, maintainability or future development of the robot.
