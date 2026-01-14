# **Week 1 Reading Material: Introduction to Embedded Systems and Development Environment**

---

## 1. Overview of Embedded Systems

An **embedded system** is a specialized computing system designed to perform specific functions within a larger mechanical or electronic system. Unlike general-purpose computers, embedded systems are dedicated to particular tasks and are often integrated into devices to control, monitor, or automate processes.

Embedded systems are widely used in:

* **Industrial automation** and control systems
* **Internet of Things (IoT)** and **Industrial IoT (IIoT)** applications
* **Measurement and monitoring** systems
* **Consumer electronics** and smart devices
* **Automotive systems** and robotics

### 1.1 What Makes Embedded Systems Unique?

Embedded systems combine **hardware** (electronic circuits and components) and **software** (firmware) to create integrated solutions. The key characteristics include:

* **Dedicated functionality** for specific applications
* **Real-time or near-real-time** operation
* **Resource constraints** (limited memory, processing power, and energy)
* **Integration** with physical processes through sensors and actuators
* **Reliability** and **deterministic behavior**

---

## 2. Embedded Systems in Measurement, Control, and Automation

This course focuses on applying **microcontrollers** to create real-world applications for **measurement, control, and automation**. Microcontrollers are compact, self-contained computers on a single integrated circuit that include a processor, memory, and programmable input/output peripherals.

### 2.1 Application Areas

**General Automation:**
* Automated control of machinery and processes
* Sensor-based monitoring and decision-making
* Actuator control for physical actions

**Industrial Internet of Things (IIoT):**
* Industrial equipment monitoring and control
* Data collection and analysis
* Remote monitoring and management

**Internet of Things (IoT):**
* Enabling microcontrollers to exchange data with mobile phones, tablets, or computers via web browsers
* Remote hardware control (e.g., turning LEDs on/off using a mobile app)
* Real-time sensor data monitoring (e.g., viewing voltage levels or switch statuses on your phone)

---

## 3. Hardware vs. Software (Firmware)

Understanding the distinction between **hardware** and **software (firmware)** is fundamental to embedded systems development.

### 3.1 Hardware

**Hardware** refers to the physical electronic components and circuits:

* **Microcontrollers** (CPU, memory, peripherals)
* **Sensors** (to measure physical quantities)
* **Actuators** (to perform physical actions)
* **Communication modules** (WiFi, serial interfaces)
* **Power supply** and **circuitry**

### 3.2 Software (Firmware)

**Firmware** is the program code that runs on the microcontroller to control its behavior:

* Written in **Embedded C** programming language
* Compiled into **machine code (Hex Code)** that the CPU understands
* Stored in **program memory** (ROM/Flash)
* Executes instructions to read sensors, process data, and control actuators

**Key Point:** Embedded systems require the **integration** of both hardware and firmware to function. The hardware provides the physical interface, while firmware provides the intelligence and control logic.

---

## 4. System Design Process

The development of embedded systems follows a systematic design process:

1. **Concept:** Define the goal and requirements
2. **Circuit Design (Schematics):** Design the electronic circuits
3. **PCB Layout:** Create the printed circuit board design
4. **3D Modeling:** Design the physical enclosure or housing
5. **Firmware Development:** Write and test the control software
6. **Integration and Testing:** Combine hardware and software, verify functionality

---

## 5. Embedded System Components and Architecture

### 5.1 CPU and Processing Units

This course uses **16-bit Microchip CPUs** (PIC24 family) as the primary processing units. These microcontrollers provide:

* Efficient processing for embedded applications
* Low power consumption
* Rich peripheral set (GPIO, timers, ADC, etc.)
* Reliable operation in industrial environments

### 5.2 WiFi Communication Modules

To enable IoT capabilities, the development boards include WiFi communication modules:

* **Generation 1:** **ESP8266** WiFi module
* **Generation 2:** **ESP32** WiFi module (with additional external memory)

These modules enable:
* Internet connectivity
* Data exchange with mobile devices and web browsers
* Remote monitoring and control capabilities

### 5.3 Development Board Generations

The course uses two generations of development boards, each designed for different learning and application purposes:

#### Generation 1: The Educator

* **Primary Use:** Training and learning with large, easy-to-see components
* **Features:**
  * 4 large LEDs for visual feedback
  * 4 switches for input
  * 4 analog input channels
  * Buzzer for audio output
* **Target Audience:** Beginners learning embedded systems fundamentals

#### Generation 2: The Powerhouse

* **Primary Use:** Compact design for advanced applications, AI models, and data processing
* **Features:**
  * 16-bit Microchip CPU + **ESP32** (integrated)
  * Built-in ESP32 with extra external memory
  * 4 small LEDs
  * Small switches
  * 2 built-in analog sensors (LDR - Light Dependent Resistor)
* **Unique Feature:** Designed as a "plugin" CPU board that can be connected to larger motherboards for specialized applications (motor driving, power supplies, control systems)

### 5.4 On-board Peripherals

Both board generations include various peripherals for hands-on learning:

* **LEDs:** Visual output indicators
* **Switches:** Digital input devices
* **Analog Sensors:** LDR (Light Dependent Resistor) for light sensing
* **Buzzer:** Audio output device
* **GPIO Pins:** General-purpose input/output for external connections

---

## 6. Development Tools and Learning Resources

### 6.1 Software Tools

**TernionDevTools (Teral Full Installer):**
* All-in-one development package
* Includes **GCC XC16 compiler** (GCC-based compiler from Microchip)
* Contains necessary libraries and development tools
* Single installation provides everything needed to start development
* Features **Build**, **Flash**, and **Monitor** commands for rapid development and debugging

**Open-Source Design Tools:**
* **KiCad:** For PCB (Printed Circuit Board) design ([Download KiCad](https://www.kicad.org/))
* **FreeCAD:** For 3D modeling and mechanical design ([Download FreeCAD](https://www.freecad.org/))
* Emphasis on open-source tools to ensure free access without licensing costs

### 6.2 Learning Resources

**GitHub Repository:**
* **Repository:** [INC342-2026](https://github.com/drsanti/INC342-2026)
* Contains: Course syllabus, detailed outline, weekly reading materials, source code examples, and documentation
* Central hub for accessing all course materials, updates, and resources

**YouTube Resources:**
* **EP1:** [Introduction to Embedded Systems](https://www.youtube.com/watch?v=R_Hrb4gQyqM&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=1)
* **EP2:** [Development Environment Overview](https://www.youtube.com/watch?v=EwJMqaTC3D0&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=2)
* Step-by-step guides for installation and programming
* Project demonstrations and explanations

---

## 7. Project-Based Learning Approach

This course uses a **"learn by doing"** (Project-Based) approach to embedded systems development.

### 7.1 Learning Philosophy

Every lesson starts with a **specific goal**—what do we want to achieve? From there, we explore two critical perspectives:

1. **Hardware Perspective:** The electronic circuits, components, and how they connect
2. **Software Perspective:** The firmware program that runs on the microcontroller to perform desired tasks

### 7.2 Learning Progression

* **Start with basics:** Software installation and simple programs (e.g., "Blinking LED")
* **Progress gradually:** Move to more complex systems and applications
* **No prior experience required:** Course starts from fundamentals
* **Hands-on practice:** Each concept is reinforced through practical exercises

### 7.3 Self-Learning and Practice Requirements

**Important Learning Guidelines:**

* **Follow step-by-step video tutorials:** Students are expected to learn and practice independently by following the step-by-step instructions provided in the video tutorials (EP1, EP2, and subsequent episodes)
* **Active participation:** Watch each video carefully and replicate the demonstrated procedures on your own development environment
* **Practice hands-on:** Type code yourself, run commands manually, and troubleshoot issues independently
* **No AI coding assistance during learning:** **Do not use AI coding assistance tools** (such as ChatGPT, GitHub Copilot, or similar AI code generators) while you are in the learning process. Using AI assistance during the learning phase prevents you from developing essential **problem-solving skills**, understanding fundamental concepts, and building the necessary expertise in embedded systems programming
* **Build foundational skills:** The goal is to develop a deep understanding of embedded systems concepts through hands-on experience, not just to complete assignments quickly

**Note:** Once you have mastered the fundamentals and understand the core concepts, you may use tools to enhance productivity in advanced projects. However, during the initial learning phase, independent practice is essential for skill development.

### 7.4 Development Workflow

The typical embedded systems development process involves:

1. **Define the goal:** What should the system do?
2. **Design hardware:** Select components and design circuits
3. **Write firmware:** Program the microcontroller
4. **Build and test:** Compile, flash, and verify functionality
5. **Iterate:** Refine and improve based on testing results

---

## 8. Course Expectations and Learning Outcomes

In this course, students will learn to:

* Understand the structure and components of embedded systems
* Set up and configure development environments
* Write firmware programs using Embedded C
* Control hardware peripherals (LEDs, switches, sensors)
* Implement event-driven programming patterns
* Apply optimization techniques for embedded systems
* Develop real-world automation and control applications

Students are expected to:

* Review technical terminology regularly
* Understand both hardware and software aspects of embedded systems
* Practice hands-on programming and hardware interfacing
* Relate programming concepts to real-world applications

---

## 9. Key Terms for Review

Before the next session, students should be familiar with the following terms:

* Embedded system
* Microcontroller
* Firmware
* Hardware vs. Software
* IoT (Internet of Things)
* IIoT (Industrial Internet of Things)
* GPIO (General-Purpose Input/Output)
* ADC (Analog-to-Digital Converter)
* Development board
* Compiler
* Machine code / Hex code

---

# Next Week

## Week 2: Development Environment Setup

### What We Will Cover

Next week, we will set up your complete development environment for embedded systems programming. This is a **hands-on session** where you will install and configure all the required software and hardware tools.

**Topics to be covered:**
* Overview of the development workflow for embedded systems
* Transition to **developer mindset** using **Command Line Interfaces (CLI)**
* Installation and configuration of required software tools:
  * **TernionDevTools (Teral Full Installer)** – Development toolchain with GCC XC16 compiler
  * **Visual Studio Code (VS Code)** – Code editor with C/C++ extension
  * **.NET 9.0** – Runtime required for TernionDevTools
* Hardware development board setup and driver installation
* Testing and verification of the development environment:
  * `ternion ls-port` – List active COM ports
  * `ternion restart` – Hardware reset verification
  * `ternion monitor` – Serial communication verification
* Introduction to debugging tools and hardware interfaces

### What to Prepare

**Before attending the class, please prepare the following:**

1. **Bring your laptop** to class (onsite students) or ensure you have access to your development machine (online students)
   * **⚠️ IMPORTANT: Must be Windows OS** – TernionDevTools only supports Windows operating system (Mac and Linux are not supported)
   * **Windows 11 is recommended** for best compatibility and performance
   * **At least one USB 2.0 port is required** for connecting the development board to your computer

2. **Administrator/Admin access** on your computer (required for software installations and hardware access)

3. **Check system requirements:**
   * **Windows operating system** (Windows 11 recommended, Windows 10 minimum) – **No Mac or Linux support for TernionDevTools**
   * **.NET 9.0** runtime ([Download .NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0))
   * **TernionDevTools (Teral Full Installer)** – Development toolchain ([Download from Google Drive](https://drive.google.com/file/d/1Npp0kykITJp_nHdoKb0izSOGRHtoLI5A/view))
   * **Visual Studio Code** ([Download VS Code](https://code.visualstudio.com/))

4. **Ensure sufficient disk space** (at least 2-3 GB free) for:
   * TernionDevTools installation
   * VS Code and extensions
   * Development tools and libraries

5. **Internet connection** (for downloading software during class)

6. **Development board** (if available):
   * Generation 1 (FTDI chip) or Generation 2 (Silicon Labs chip)
   * USB cable for connection

7. **Optional but recommended:**
   * Familiarize yourself with basic terminal/command line usage
   * Review the GitHub repository: [INC342-2026](https://github.com/drsanti/INC342-2026)

**Note:** We will guide you through the installation process step-by-step during the class. The TernionDevTools installer can be downloaded from [Google Drive](https://drive.google.com/file/d/1Npp0kykITJp_nHdoKb0izSOGRHtoLI5A/view).

**Important:** The TernionDevTools installer must be **Run as Administrator** for proper hardware access, and you will need to run `ternion install` to add environment paths.

---

## **Self-Assessment**

After reading this material, please review the key concepts covered in this week's reading material:

* Embedded systems and their applications
* Hardware vs. Software (Firmware)
* Development board generations and components
* Project-based learning approach
* Development tools and resources

Consider how embedded systems differ from general-purpose computers and why they are essential for automation and IoT applications.

---

**Last Updated:** 2026-01-13

---
