#Wearable Dosimeter

A wearable redesign of the OpenDosimeter platform focused on compact electronics, custom PCB integration, embedded firmware, and practical radiation-monitoring applications.

Overview

The Wearable OpenDosimeter is a redesigned and wearable implementation of the OpenDosimeter concept. The project takes the original open-source dosimeter architecture and re-engineers it around a compact, portable form factor intended to be worn by the user.

The redesign brings together:

Embedded systems and firmware development

Custom PCB design and redesign

Radiation sensing and measurement

Power management

Mechanical and enclosure design

Human-centered wearable integration

Hardware and software testing

The main objective was not simply to reproduce the original device, but to explore how its electronics and mechanical architecture could be adapted into a more compact and wearable platform.

Project Motivation

Traditional prototype radiation-monitoring systems can become inconvenient when the electronics, battery, sensor, and user interface are separated into a relatively large enclosure.

This project explores a different approach: integrating the sensing, processing, power, and user-interface subsystems into a compact wearable device.

The redesign therefore focuses on three major engineering challenges:

Electronics integration — fitting the required circuitry into a smaller custom PCB.

Wearability — designing the physical system around a form factor that can be comfortably carried or worn.

System integration — ensuring that sensing, processing, power, firmware, and mechanical components work together as one system.

Project Goals

The primary goals of the project are:

Redesign the original OpenDosimeter electronics for a wearable implementation.

Develop a compact custom PCB.

Integrate the radiation-sensing subsystem with the embedded controller.

Implement firmware for sensor acquisition and measurement processing.

Provide a practical user interface for viewing measurements.

Integrate rechargeable battery power and power management.

Develop a compact mechanical enclosure.

Create a modular hardware and firmware architecture that can be extended in future revisions.

Maintain clear documentation to support further development.

Key Features

Wearable form factor

Custom PCB

Embedded microcontroller

Radiation sensing

Real-time measurement processing

On-device display/interface

Rechargeable battery operation

Integrated power management

Compact electronics and mechanical integration

Modular firmware architecture

Expandable data logging and communication architecture

System Architecture

The system is organized into several functional layers: sensing, processing, user interface, data handling, and power management.

flowchart TB
    subgraph SENSING["Sensing Layer"]
        RAD["Radiation Sensor"]
    end

    subgraph PROCESSING["Processing Layer"]
        MCU["Microcontroller"]
        DSP["Signal Processing<br/>Measurement Calculation"]
    end

    subgraph INTERFACE["User Interface"]
        DISP["Display"]
        ALERT["Alerts / Indicators"]
    end

    subgraph DATA["Data & Connectivity"]
        LOG["Data Logging"]
        COMM["Communication Interface"]
    end

    subgraph POWER["Power System"]
        BAT["Rechargeable Battery"]
        PMIC["Power Management"]
    end

    RAD --> MCU
    MCU --> DSP

    DSP --> DISP
    DSP --> ALERT
    DSP --> LOG
    MCU --> COMM

    BAT --> PMIC
    PMIC --> MCU
    PMIC --> RAD
    PMIC --> DISP

The architecture separates the device into logical subsystems so that individual components can be modified without requiring a complete redesign of the system.

Hardware Architecture

The hardware can be viewed as five major sections:

1. Radiation Detection

The radiation sensor detects ionizing radiation and produces an electrical signal that can be captured and processed by the microcontroller.

The sensing subsystem is one of the most important parts of the device because measurement quality depends on the sensor, signal conditioning, acquisition method, calibration, and physical configuration.

2. Processing

The microcontroller serves as the central processing unit.

It handles:

Sensor acquisition

Signal processing

Measurement calculations

Display updates

System control

Power-management logic

Communication with external systems

3. User Interface

The user interface provides a convenient way to observe radiation measurements and system status directly from the wearable device.

Depending on the hardware revision, this can include:

Display output

Status indicators

Audible or visual alerts

User input controls

4. Data and Communication

The architecture can support data logging and communication interfaces for future expansion.

Potential interfaces include:

Serial communication

USB

Bluetooth

Wi-Fi

External data logging

5. Power Management

The wearable is designed around rechargeable battery operation.

The power subsystem is responsible for:

Battery input

Voltage regulation

Power distribution

Charging

Protection

Power-state management

Firmware Architecture

The firmware follows a continuous measurement-and-processing cycle.

flowchart TD
    A["System Startup"] --> B["Initialize Hardware"]
    B --> C["Initialize Radiation Sensor"]
    C --> D["Initialize Display & Peripherals"]
    D --> E["Begin Measurement"]

    E --> F["Acquire Sensor Data"]
    F --> G["Process & Validate Data"]
    G --> H["Calculate Radiation Measurements"]

    H --> I["Update Display"]
    H --> J["Store Measurement Data"]
    H --> K["Generate Alerts"]

    I --> L{"Continue Monitoring?"}
    J --> L
    K --> L

    L -->|"Yes"| F
    L -->|"No"| M["Safe Shutdown"]

The firmware is designed around a repeated acquisition and processing loop. This allows the device to continuously monitor the radiation sensor while updating the user interface and other system functions.

Measurement Pipeline

The general measurement pipeline is:

flowchart LR
    A["Radiation Event"] --> B["Radiation Sensor"]
    B --> C["Electrical Signal"]
    C --> D["Microcontroller"]
    D --> E["Signal Processing"]
    E --> F["Measurement Calculation"]
    F --> G["User Interface"]
    F --> H["Data Storage"]
    F --> I["Alert System"]

This separation makes it possible to improve the signal-processing or measurement algorithms without fundamentally changing the mechanical enclosure.

PCB Redesign

A major part of the project is the redesign of the electronics around a wearable form factor.

The PCB redesign considers:

Component placement

PCB dimensions

Sensor connections

Power distribution

Grounding

Signal routing

Connector placement

Programming/debugging access

Battery connections

Mechanical mounting

Enclosure constraints

Manufacturability

The PCB and mechanical enclosure are treated as a combined system rather than as independent designs.

PCB Design Priorities

The redesign prioritizes:

Compactness

Reducing unnecessary board area to make the final device easier to wear.

Serviceability

Maintaining reasonable access to programming, debugging, charging, and important electrical connections.

Signal Integrity

Keeping sensitive measurement and digital circuitry appropriately routed and powered.

Mechanical Integration

Positioning connectors, displays, sensors, and mounting points according to the enclosure geometry.

Mechanical & Wearable Design

The mechanical redesign converts the electronics from a general-purpose prototype into a wearable platform.

The enclosure is designed around:

PCB dimensions

Battery dimensions

Sensor location

Display visibility

Connector access

User interaction

Mechanical protection

Wearability

The mechanical system should also provide sufficient protection for the electronics while avoiding unnecessary bulk.

flowchart TB
    A["Wearable Enclosure"] --> B["Custom PCB"]
    A --> C["Rechargeable Battery"]
    A --> D["Radiation Sensor"]
    A --> E["Display / User Interface"]
    A --> F["Charging & I/O Access"]

    B --> G["Electrical Integration"]
    C --> G
    D --> G
    E --> G
    F --> G

Engineering Workflow

The project follows an iterative engineering workflow:

flowchart LR
    A["Requirements"] --> B["System Architecture"]
    B --> C["Circuit & PCB Design"]
    C --> D["Mechanical Design"]
    D --> E["Prototype"]
    E --> F["Firmware Integration"]
    F --> G["Testing"]
    G --> H["Validation"]
    H --> I{"Issues Found?"}
    I -->|"Yes"| C
    I -->|"No"| J["Revision / Final Prototype"]

This iterative approach allows electrical, firmware, and mechanical problems to be identified early and incorporated into subsequent revisions.

Development Tools

The project can be developed using a combination of hardware, firmware, CAD, and documentation tools.

Area

Tools / Technologies

PCB Design

KiCad

Firmware

C / C++

Embedded Development

PlatformIO / Arduino-compatible workflow

Data Processing

Python

Mechanical Design

CAD software

Version Control

Git / GitHub

Documentation

Markdown

Prototyping

PCB fabrication, 3D printing and laboratory equipment

The exact tools may vary between hardware revisions.

Suggested Repository Structure

Wearable-OpenDosimeter/
│
├── firmware/
│   ├── src/
│   ├── include/
│   ├── lib/
│   └── platformio.ini
│
├── hardware/
│   ├── schematic/
│   ├── pcb/
│   ├── gerbers/
│   └── bom/
│
├── mechanical/
│   ├── cad/
│   ├── enclosure/
│   └── drawings/
│
├── documentation/
│   ├── design/
│   ├── testing/
│   └── calibration/
│
├── images/
│   ├── pcb/
│   ├── enclosure/
│   └── prototype/
│
├── tests/
│
├── LICENSE
└── README.md

Testing & Validation

Testing should be performed progressively rather than attempting to validate the complete device at once.

Electrical Testing

Verify:

Supply voltages

Current consumption

Battery operation

Charging behavior

Regulator outputs

GPIO functionality

Communication interfaces

PCB connectivity

Firmware Testing

Verify:

Sensor initialization

Sensor data acquisition

Measurement calculations

Display operation

Error handling

Communication

Power-management behavior

Mechanical Testing

Verify:

PCB fit

Battery fit

Connector accessibility

Sensor placement

Enclosure assembly

Wearability

Mechanical robustness

Measurement Validation

Radiation measurements should be evaluated using appropriate calibration and validation procedures.

Important factors include:

Sensor response

Radiation source characteristics

Radiation energy

Measurement geometry

Environmental conditions

Sensor-to-source distance

Electronics response

Statistical variation

Calibration

Accurate radiation measurement requires appropriate calibration.

A calibration procedure should establish the relationship between the sensor's electrical response and the radiation quantity being reported.

Depending on the measurement architecture, calibration may involve:

Establishing a controlled measurement setup.

Recording sensor output under known conditions.

Repeating measurements to evaluate variability.

Developing the required conversion relationship.

Validating the resulting measurements against an appropriate reference.

Documenting calibration conditions and limitations.

Calibration results should be stored alongside the relevant firmware and hardware revision where possible.

Safety & Measurement Disclaimer

This project is intended primarily for educational, research, and prototyping purposes.

A prototype radiation detector should not automatically be considered a certified radiation-protection instrument.

For applications involving occupational exposure, medical use, regulatory compliance, or other safety-critical decisions, the device would require appropriate calibration, validation, certification, and compliance with applicable standards and regulations.

Design Philosophy

The project is guided by several engineering principles:

Modularity

Hardware, firmware, and mechanical components should remain modular so that future revisions can replace individual subsystems without redesigning the entire platform.

Iterative Development

The device is developed through repeated cycles of design, fabrication, testing, measurement, and improvement.

Human-Centered Engineering

The redesign considers how the device will actually be worn, interacted with, maintained, and used rather than optimizing only for laboratory functionality.

Open Development

Where permitted by the original project license, design files and documentation should remain accessible so that other developers and researchers can study and improve the platform.

Future Improvements

Potential future development areas include:

Improved radiation sensor integration

Improved calibration procedures

Smaller PCB revisions

Lower-power operation

Extended battery life

Wireless data transmission

Mobile application integration

Cloud-based measurement logging

GPS-based radiation mapping

Improved enclosure ergonomics

Haptic, audible, or visual alerts

More advanced measurement algorithms

Automated test procedures

Improved manufacturing documentation

Project Status

Status: Prototype / Research & Development

The current project represents a redesign of the OpenDosimeter concept into a wearable platform. The hardware, firmware, PCB, mechanical enclosure, and measurement system can continue to evolve through additional testing and design iterations.

Contribution

The project involves work across multiple engineering disciplines, including:

Embedded systems

Firmware development

PCB design and redesign

Electrical hardware integration

Mechanical integration

Wearable product design

System testing

Technical documentation

The redesign focuses particularly on integrating these disciplines into a single compact device.

Acknowledgements

This project is based on the concept and work of the OpenDosimeter open-source project.

The original project's contributors and open-source community are acknowledged for providing the foundation on which this wearable redesign is being explored.

Where original OpenDosimeter hardware, firmware, documentation, or design elements are retained, the applicable original licensing and attribution requirements should be preserved.

Author

George Wambugu Mwangi

BSc Mechatronics Engineering
Dedan Kimathi University of Technology (DeKUT), Kenya

Areas of Contribution

Embedded Systems

Firmware Development

PCB Redesign

Hardware Integration

Mechanical Integration

Wearable Device Development

System Testing

Technical Documentation
