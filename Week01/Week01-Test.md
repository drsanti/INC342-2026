# **Week 1 Self-Test Quiz**

**Topic: Introduction to Embedded Systems and Development Environment**

---

## **Questions**

### **1. Short Answer**

What is an **embedded system**, and how does it differ from a general-purpose computer?

---

### **2. Multiple Choice**

Which of the following best describes the key characteristics of embedded systems?

A. High memory capacity, unlimited processing power, and flexible functionality
B. Dedicated functionality, resource constraints, and integration with physical processes
C. General-purpose computing, user-friendly interfaces, and multitasking capabilities
D. Cloud-based processing, unlimited energy consumption, and network-dependent operation

---

### **3. True or False**

**Firmware** is the physical electronic components and circuits that make up an embedded system.

---

### **4. Short Answer**

What is the difference between **hardware** and **firmware** in embedded systems?

---

### **5. Multiple Choice**

This course uses which type of microcontrollers as the primary processing units?

A. 8-bit ARM processors
B. 16-bit Microchip CPUs (PIC24 family)
C. 32-bit Intel processors
D. 64-bit x86 processors

---

### **6. Short Answer**

What are the main differences between **Generation 1** and **Generation 2** development boards used in this course?

---

### **7. True or False**

**Generation 2** development boards are designed as "plugin" CPU boards that can be connected to larger motherboards for specialized applications.

---

### **8. Multiple Choice**

Which WiFi communication module is used in **Generation 1** development boards?

A. ESP32
B. ESP8266
C. Wi-Fi 6 module
D. Bluetooth module

---

### **9. Short Answer**

List the **six steps** of the embedded systems design process in order.

---

### **10. Multiple Choice**

What does **TernionDevTools (Teral Full Installer)** include?

A. Only the GCC XC16 compiler
B. GCC XC16 compiler, libraries, and development tools in a single package
C. Only development libraries
D. Only debugging tools

---

### **11. True or False**

Students should use AI coding assistance tools (such as ChatGPT or GitHub Copilot) during the initial learning phase to complete assignments quickly.

---

### **12. Short Answer**

What is the **"learn by doing"** (Project-Based) approach, and what are the two critical perspectives explored in this course?

---

### **13. Multiple Choice**

Which of the following is **NOT** a typical application area for embedded systems covered in this course?

A. Industrial automation and control systems
B. Internet of Things (IoT) and Industrial IoT (IIoT) applications
C. Desktop application development
D. Measurement and monitoring systems

---

### **14. Short Answer**

What is the role of **firmware** in an embedded system, and what programming language is used to write it?

---

### **15. Scenario-Based Question**

A student wants to create an embedded system that monitors light levels using a sensor and automatically adjusts LED brightness. The system should also be able to send data to a mobile phone via WiFi.

Based on the Week 1 reading material, explain:
1. Which development board generation would be most suitable and why?
2. What are the key hardware and firmware components needed?
3. What is the first step in the system design process?

---

## **Answers**

### **1.**

An **embedded system** is a specialized computing system designed to perform specific functions within a larger mechanical or electronic system. Unlike general-purpose computers, embedded systems are dedicated to particular tasks, have resource constraints (limited memory, processing power, and energy), and are often integrated into devices to control, monitor, or automate processes.

---

### **2.**

**B.** Dedicated functionality, resource constraints, and integration with physical processes

Embedded systems are characterized by dedicated functionality for specific applications, resource constraints (limited memory, processing power, and energy), and integration with physical processes through sensors and actuators.

---

### **3.**

**False**

**Firmware** is the program code (software) that runs on the microcontroller to control its behavior. Hardware refers to the physical electronic components and circuits. Firmware is written in Embedded C, compiled into machine code, and stored in program memory.

---

### **4.**

**Hardware** refers to the physical electronic components and circuits, including microcontrollers (CPU, memory, peripherals), sensors, actuators, communication modules, power supply, and circuitry.

**Firmware** is the program code (software) that runs on the microcontroller to control its behavior. It is written in Embedded C programming language, compiled into machine code (Hex Code), stored in program memory (ROM/Flash), and executes instructions to read sensors, process data, and control actuators.

The key difference: Hardware provides the physical interface, while firmware provides the intelligence and control logic. Both are required for embedded systems to function.

---

### **5.**

**B.** 16-bit Microchip CPUs (PIC24 family)

This course uses 16-bit Microchip CPUs (PIC24 family) as the primary processing units, which provide efficient processing for embedded applications, low power consumption, rich peripheral sets (GPIO, timers, ADC, etc.), and reliable operation in industrial environments.

---

### **6.**

**Generation 1 (The Educator):**
- Primary use: Training and learning with large, easy-to-see components
- Features: 4 large LEDs, 4 switches, 4 analog input channels, buzzer
- WiFi module: ESP8266
- Target audience: Beginners learning embedded systems fundamentals

**Generation 2 (The Powerhouse):**
- Primary use: Compact design for advanced applications, AI models, and data processing
- Features: 4 small LEDs, small switches, 2 built-in analog sensors (LDR)
- WiFi module: ESP32 (integrated) with extra external memory
- Unique feature: Designed as a "plugin" CPU board that can be connected to larger motherboards for specialized applications

---

### **7.**

**True**

Generation 2 development boards are designed as "plugin" CPU boards that can be connected to larger motherboards for specialized applications such as motor driving, power supplies, and control systems.

---

### **8.**

**B.** ESP8266

Generation 1 development boards use the ESP8266 WiFi module, while Generation 2 boards use the ESP32 WiFi module (with additional external memory).

---

### **9.**

The six steps of the embedded systems design process are:

1. **Concept:** Define the goal and requirements
2. **Circuit Design (Schematics):** Design the electronic circuits
3. **PCB Layout:** Create the printed circuit board design
4. **3D Modeling:** Design the physical enclosure or housing
5. **Firmware Development:** Write and test the control software
6. **Integration and Testing:** Combine hardware and software, verify functionality

---

### **10.**

**B.** GCC XC16 compiler, libraries, and development tools in a single package

TernionDevTools (Teral Full Installer) is an all-in-one development package that includes the GCC XC16 compiler (GCC-based compiler from Microchip), necessary libraries, and development tools. A single installation provides everything needed to start development, and it features Build, Flash, and Monitor commands for rapid development and debugging.

---

### **11.**

**False**

Students should **NOT** use AI coding assistance tools during the initial learning phase. Using AI assistance during the learning phase prevents students from developing essential problem-solving skills, understanding fundamental concepts, and building the necessary expertise in embedded systems programming. The goal is to develop a deep understanding through hands-on experience, not just to complete assignments quickly.

---

### **12.**

The **"learn by doing"** (Project-Based) approach means that every lesson starts with a specific goal—what do we want to achieve? From there, students explore two critical perspectives:

1. **Hardware Perspective:** The electronic circuits, components, and how they connect
2. **Software Perspective:** The firmware program that runs on the microcontroller to perform desired tasks

This approach emphasizes hands-on practice, starting with basics (like software installation and simple programs) and gradually progressing to more complex systems and applications.

---

### **13.**

**C.** Desktop application development

Desktop application development is not a typical application area for embedded systems. The course focuses on industrial automation, IoT/IIoT applications, measurement and monitoring systems, consumer electronics, automotive systems, and robotics—all of which involve embedded systems integrated into devices for specific control, monitoring, or automation tasks.

---

### **14.**

**Firmware** is the program code that runs on the microcontroller to control its behavior. Its role includes:
- Reading sensor data
- Processing information
- Controlling actuators
- Executing the control logic and decision-making

Firmware is written in **Embedded C** programming language, which is then compiled into machine code (Hex Code) that the CPU understands, and stored in program memory (ROM/Flash).

---

### **15.**

**1. Development Board Selection:**
**Generation 2 (The Powerhouse)** would be most suitable because:
- It has built-in ESP32 WiFi module with extra external memory, enabling WiFi communication with mobile phones
- It includes 2 built-in analog sensors (LDR - Light Dependent Resistor) for light sensing
- It has LEDs for brightness control
- It is designed for advanced applications and data processing, which aligns with the IoT requirements

**2. Key Components Needed:**

**Hardware:**
- Microcontroller (16-bit Microchip CPU)
- Light sensor (LDR - already built into Gen 2, or external sensor)
- LEDs (for brightness control)
- WiFi module (ESP32 - built into Gen 2)
- Power supply and circuitry

**Firmware:**
- Embedded C program to:
  - Read light sensor values (ADC)
  - Process sensor data
  - Control LED brightness based on light levels
  - Handle WiFi communication to send data to mobile phone
  - Implement control logic and decision-making

**3. First Step in System Design Process:**
The first step is **Concept:** Define the goal and requirements. In this case, the goal is to create a light monitoring system with automatic LED brightness adjustment and WiFi connectivity for mobile phone data transmission. This step involves clearly defining what the system should do, its requirements, and its constraints.

---

**Last Updated:** 2026-01-13

---
