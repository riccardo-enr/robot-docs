---
title: Lynx Firmware
parent: Lynx
---

# Flashing the firmware

Firmware flashing should be done using [PlatformIO](https://platformio.org/), an extension for Visual Studio Code (VSCode).

# Important Considerations for Firmware

- **Devastator vs. Lynx Configurations**:
    - Different configurations (e.g., Devastator or Lynx) may require adjustments to the **encoders**.
    - Verify that the **PWM pins** used for each configuration match those defined in the code.
        - *Tip*: Refer to the documentation or source files to locate the correct pins.

## Help Section in the Main File

At the beginning of the `main` file, there is a **help section** that can be referenced if you have any questions or uncertainties. Although I have marked specific lines in the code, please note that this information may not be up-to-date.

# Main File Analysis

## Sensor Calibration Functions
Within the `main` file, several methods/functions are dedicated to **calibrating all sensors**. Each sensor is managed through a specific **driver** (written as separate `.cpp` files), which are adapted from existing codebases. These drivers are already well-documented.

## PWMPort Details
The `PWMPort` element appears to be a **thread**—possibly a custom-defined class (this will require further review). `PWMPort` is used to **assign pins on the Freedom Board** for controlling actuators and reading sensors. It may be connected to an **H-bridge** for motor control or similar tasks.

## SD Card Requirement
An **SD card** is required for:
- **Storing calibration values**
- **Logging sensor data**

# MAVLink Messages

To view and verify the MAVLink messages sent to the computer, check the file located at `./src/mavlink_comm.cpp`. This file contains **MAVLink message definitions**. Additionally, there is a MAVLink website that provides definitions for all MAVLink messages, which can be helpful for reference.

# User Guide

## Operating on the Main Computer
All operations are managed from the main computer, where the relevant messages can be read. To double-check definitions directly from the firmware, refer to the `./src/sensors/sensor.cpp` file.

## Powering On the Lynx

- **Flashing the Freedom Board**: Flashing does not require any additional power setup; the board can be flashed without turning on any additional components.
- **Hardware Power Line**: The power line for the hardware components is pre-configured and does not require further setup.
