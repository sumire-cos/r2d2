# MQTT Communication Topics

## 1. Overview

This document describes the MQTT topics used by the R2-D2 robot.

The Raspberry Pi runs independent software modules that exchange commands through an MQTT broker. The broker currently used is Mosquitto.

This document distinguishes implemented communication from future integrations. Payload formats are only specified where they have been confirmed.

## 2. MQTT Broker

| Component | Configuration |
|---|---|
| Broker | Mosquitto |
| Host | Raspberry Pi |
| Local address | localhost |
| Protocol | MQTT |

The broker runs locally on the Raspberry Pi. Modules publish messages to topics, and the relevant modules subscribe to those topics.

## 3. Operational Topics

### 3.1 Track Drive

**Topic:** `robot/drive`

| Property | Description |
|---|---|
| Publisher | Controller module |
| Subscriber | Track motor module |
| Status | Operational |
| Purpose | Sends movement commands to the two track motors |

The controller module publishes movement commands. The motor module subscribes to this topic and controls the left and right track motors.

The exact payload schema should be maintained from the implementation and is not specified here.

### 3.2 Audio Playback

**Topic:** `robot/audio/play`

| Property | Description |
|---|---|
| Publisher | Controller module |
| Subscriber | Audio module |
| Status | Operational |
| Purpose | Requests playback of a sound |

The controller module publishes audio playback requests. The audio module receives these requests and plays the corresponding sound.

The exact payload schema should be maintained from the implementation and is not specified here.

### 3.3 Dome Rotation

**Topic:** `robot/dome/rotation`

<badge>Operational</badge>

| Property | Description |
|---|---|
| Publisher | Controller module |
| Subscriber | Dome rotation module |
| Module path | `modules/rotation_dome/` |
| Main file | `rotation_dome.py` |
| Motor driver | L298N, second driver board, channel A |
| System service | `rotation_dome.service` |
| GPIO direction pins | GPIO 5 and GPIO 6 |
| GPIO PWM pin | GPIO 16 |
| Status | Implemented and tested |

The Raspberry Pi directly controls the motor that rotates the dome relative to the robot's body.

The motor is connected to channel A of the second L298N board. The rotation module is independent of the track drive module.

#### Payload

The topic uses a JSON object containing the `speed` field.

| Example payload | Meaning |
|---|---|
| `{"speed": 0.2}` | Rotate in one direction |
| `{"speed": -0.2}` | Rotate in the opposite direction |
| `{"speed": 0}` | Stop rotation |

Positive and negative values select opposite rotation directions. A value of zero stops the motor. The examples above are representative tested commands; this document does not define an unverified numeric speed range.

## 4. Current Communication Overview

```text
                         Raspberry Pi 4
                               |
                        MQTT Broker
                          Mosquitto
                               |
             +-----------------+-----------------+
             |                 |                 |
        robot/drive     robot/audio/play  robot/dome/rotation
             |                 |                 |
       Track motor        Audio module      Dome rotation
         module                                  module
             |                 |                 |
       Track motors       HiFiBerry DAC     Second L298N
                                                  |
                                          Dome rotation motor
```

The controller module publishes commands to the broker. The track motor, audio and dome rotation modules subscribe to their respective topics.

## 5. Future Dome Mechanisms

The rotation of the dome is already controlled by the Raspberry Pi through `robot/dome/rotation`.

This is separate from the mechanisms located inside the dome. Their future control is planned around a dedicated ESP32 controller.

The MQTT topic or topics and payload formats for those internal mechanisms have not yet been finalized. They must be documented once the communication architecture is implemented and tested.

## 6. Payload Documentation

| Topic | Payload format | Status |
|---|---|---|
| `robot/drive` | To be documented from source code | Operational |
| `robot/audio/play` | To be documented from source code | Operational |
| `robot/dome/rotation` | JSON object with a `speed` field | Operational |

Do not assume a payload structure that has not been checked against the corresponding module.

## 7. Development Guidelines

When introducing or changing an MQTT topic:

1. Use a clear and consistent topic name.
2. Document its purpose.
3. Identify the publishing module.
4. Identify all subscribing modules.
5. Document the payload format and representative values.
6. Test the communication between modules.
7. Update this document.

## 8. Future Updates

Update this document whenever:

- A new MQTT topic is introduced.
- A topic is renamed or removed.
- A message payload changes.
- A module starts or stops publishing or subscribing.
- The MQTT broker configuration changes.
- A planned subsystem becomes operational.
