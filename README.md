# Arduino-Based Vehicle Safety System with Alcohol Detection

A comprehensive fail-safe ignition control system that prevents intoxicated drivers from starting their vehicles using Arduino-based alcohol detection, event logging, and intelligent fail-safe logic.

## Project Overview

This system is designed to enhance vehicle safety by:
- **Alcohol Detection**: Real-time monitoring of alcohol vapors using an analog sensor
- **Fail-Safe Ignition Logic**: Prevents engine start if alcohol levels exceed safe thresholds
- **Event Logging**: Records all system events with timestamps to EEPROM for audit trails
- **Real-time Display**: LCD display shows current system status and sensor readings
- **Calibration System**: Serial-based calibration for sensor baseline and thresholds
- **Fault Detection**: Identifies sensor malfunctions and blocks engine for safety

## Features

### Core Functionality
- **Alcohol Sensor Monitoring**: Continuous analog input monitoring with configurable thresholds
- **Relay-Based Ignition Control**: GPIO-controlled relay for engine start/stop
- **Audible Alerts**: Buzzer alerts for different system states
- **Real-time Clock (RTC)**: DS3231 for precise timestamped event logging
- **EEPROM Storage**: Non-volatile storage for event logs and calibration settings
- **LCD Display**: 16x2 I2C LCD for user interface and status display

### Safety Features
- Sensor fault detection (open/short circuit identification)
- Fail-safe engine blocking on system errors
- RTC validation with automatic time adjustment
- Circular event logging with configurable capacity
- Pull-up configuration for ignition switch

### Configuration & Monitoring
- **Serial Commands**: 
  - `readlogs` - Retrieve stored event logs
  - `clearlogs` - Clear event history
  - `calibrate` - Calibrate sensor baseline and threshold
  - `plotmode on/off` - Enable/disable data plotting mode
  - `help` - Display command help
- **Calibration Wizard**: Step-by-step guided sensor calibration
- **Real-time Mode**: Optional plot mode for sensor data visualization

## Hardware Components

| Component | Pin | Type | Purpose |
|-----------|-----|------|---------|
| Alcohol Sensor | A0 | Analog Input | Detects alcohol vapor levels |
| Relay | 7 | Digital Output | Controls engine ignition |
| Buzzer | 8 | Digital Output | Audible alerts |
| Ignition Switch | 9 | Digital Input (Pull-up) | Engine start request |
| RTC (DS3231) | SDA/SCL | I2C | Timestamp all events |
| LCD (16x2) | SDA/SCL | I2C | Status display |

## System Status Codes

- **STATUS_SAFE (0)**: Alcohol levels within safe threshold
- **STATUS_ALCOHOL (1)**: Alcohol detected above threshold - engine blocked
- **STATUS_FAULT (2)**: Sensor fault detected
- **STATUS_WARNING (3)**: Warning condition
- **STATUS_IGN_ON (4)**: Ignition turned on
- **STATUS_IGN_OFF (5)**: Ignition turned off

## Default Configuration

- Alcohol Threshold: 400 (analog units)
- Sensor Fault Min: 5 (open circuit threshold)
- Sensor Fault Max: 1018 (short circuit threshold)
- EEPROM Log Size: 128 entries (10 bytes per entry)

## Event Logging

Each logged event contains:
- Status code (1 byte)
- Sensor value (2 bytes)
- Timestamp - Year, Month, Day, Hour, Minute, Second (6 bytes)

## Serial Interface

- Baud rate: 9600
- Default commands for debugging and configuration
- Real-time sensor data output for monitoring

## Files in This Repository

- **code.txt** - Main Arduino sketch
- **Block_Diagram.png** - System architecture diagram
- **working_logic.png** - Logic flow diagram
- **Report.docx** - Detailed technical documentation
- **README.md** - This file

## Getting Started

1. Connect the Arduino and all components according to the hardware pinout
2. Upload the sketch to your Arduino
3. Power on the system and observe LCD initialization
4. Use serial commands to calibrate the sensor
5. System will automatically block engine start if alcohol is detected

## Safety Notes

- **Critical**: Do not bypass fail-safe mechanisms
- **Testing Only**: Ensure proper calibration before operational use
- **Maintenance**: Regularly verify sensor functionality
- **Legal**: Comply with local regulations when deploying this system

## Contributing

For bug reports or feature requests, refer to the documentation in Report.docx for detailed system specifications.