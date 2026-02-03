# INC342: Embedded Systems and Applications

> This course introduces **embedded systems** and their applications in **measurement, control, and automation**. Students will gain both **theoretical knowledge** and **practical programming skills** through a progressive three-phase learning approach: **foundations** (embedded system concepts, development environment setup, firmware development, and event-driven programming), **embedded C programming** (advanced C techniques, pointers, memory management, and microcontroller peripherals), and **advanced techniques** (program flow control, I/O manipulation, code optimization, and advanced programming patterns). The course emphasizes **hands-on development** of **firmware applications** using **16-bit Microchip microcontrollers** and **Embedded C programming** for real-world automation and control applications.

---

[**Syllabus**](./Syllabus.md) | [**Course Outline**](./Outline.md) | [**Weekly Materials**](#weekly-reading-materials--self-test-quizzes) | [**YouTube**](https://www.youtube.com/watch?v=R_Hrb4gQyqM&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj) | [**GitHub**](https://github.com/drsanti/INC342-2026)

![Course Code](https://img.shields.io/badge/Course-INC342-blue) ![Year](https://img.shields.io/badge/Year-2026-green) ![Language](https://img.shields.io/badge/Language-Embedded%20C-orange)

---

![alt text](assets/cover.png)

---

## Course Information

| **Details** | **Information** |
|------------|----------------|
| **Learning Format** | Hybrid (Onsite + Online) |
| **Classroom (Onsite)** | CB40610(1) |
| **Schedule** | A/Section 1: **Friday**, **09:30 – 16:30**<br>B/Section 2: **Wednesday**, **13:30 – 16:30** |
| **Evaluation** | Assignments: **20%**, Quizzes: **80%**|

### **Online Meeting Links (Zoom)**

**A/Section 1:**
- **Zoom Meeting:** [Join Meeting](https://kmutt-ac-th.zoom.us/j/94624481996?pwd=dCXxDVdXpAmxwvUFCPVHWtfNc6WKkM.1)
- **Meeting ID:** 946 2448 1996
- **Passcode:** 423767

**B/Section 2:**
- **Zoom Meeting:** [Join Meeting](https://kmutt-ac-th.zoom.us/j/99669736240?pwd=xLBOXXRlArcNBpPHokBXO563xhye6D.1)
- **Meeting ID:** 996 6973 6240
- **Passcode:** 577780

---


## Course Description

This course covers the principles and applications of **embedded systems** for automation and control. Topics include **embedded system components** and architecture (16-bit Microchip CPUs, WiFi modules, board generations), **development environment setup** (CLI usage, TernionDevTools, IDE configuration), **firmware development** (development workflow, build/compile process, project structure), and **Embedded C programming fundamentals** (syntax, memory management, essential functions). The course also explores **event-driven programming** (events, callbacks, timers, state machines, ADC), **advanced Embedded C techniques** (standardized data types, pointers, memory management, `typedef`, data integrity), **microcontroller peripherals programming** (GPIO operations, register-level control), **program flow control and I/O manipulation** (conditional statements, Sensor-Controller-Actuator model, Digital/Analog I/O, bit manipulation), **code optimization strategies** (execution speed, memory/program length optimization, best practices), and **advanced programming techniques** (real-time timing, event-driven task scheduling, state machine architecture, modular peripheral control). Emphasis is placed on **hands-on programming** and **project-based learning** for real-world automation applications.

---

## Learning Outcomes

Upon successful completion of this course, students will be able to:

1. **Explain** the structure and components of **embedded systems** for automation and control applications, including hardware vs. software (firmware), system design process, and embedded system architecture.
2. **Design and develop firmware programs** using **Embedded C programming** to control devices, machinery, and automation systems, including event-driven applications, peripheral control, and I/O manipulation.
3. **Apply code optimization techniques** and **advanced programming patterns** (state machines, modular control, real-time timing) to create efficient embedded system applications for industrial automation.

---

## Course Resources

### **Course Documents**
- **[Syllabus](./Syllabus.md)** - Complete course syllabus with detailed information
- **[Course Outline](./Outline.md)** - Weekly schedule and topics

### **Learning Resources**
- **YouTube Playlist:** [EP01-EP20](https://www.youtube.com/watch?v=R_Hrb4gQyqM&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj)
- **GitHub Repository:** [INC342-2026](https://github.com/drsanti/INC342-2026) - Learning resources, software tools, and documents

### **Weekly Reading Materials & Self-Test Quizzes**

Weekly reading materials and self-test quizzes are available to help you prepare for classes and assess your understanding:

**Week 1: Introduction to Embedded Systems and Development Environment**
- 📖 [Reading Material](./Week01/Week01-Read.md)
- ✅ [Self-Test Quiz](./Week01/Week01-Test.md)

**Week 2: Development Environment Setup**
- 📖 [Reading Material](./Week02/Week02-Read.md)
- ✅ [Self-Test Quiz](./Week02/Week02-Test.md)

**Week 3: Firmware Development and Embedded C Programming**
- 📖 [Reading Material](./Week03/Week03-Read.md)
- ✅ [Self-Test Quiz](./Week03/Week03-Test.md)

**Week 4: Introduction to Event-Driven Programming**
- 📖 [Reading (concepts)](./Week04/Week04-Read01.md) — Periodic operations, events, ADC
- 📖 [Code examples](./Week04/Week04-Read02.md) — EP8, EP9, EP10 (blinking LED, switch, ADC)
- ✅ [Self-Test (concepts)](./Week04/Week04-Test01.md)
- ✅ [Self-Test (code)](./Week04/Week04-Test02.md)
- 📋 [Week 4 folder index](./Week04/README.md)

**Note:** Additional weekly materials will be added as the course progresses.

---

## Technologies & Tools

This course uses the following technologies and tools:

- **.NET 9.0** - Runtime required for TernionDevTools ([Download .NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0))
- **TernionDevTools (Teral Full Installer)** - Development toolchain including GCC XC16 compiler, libraries, and tools ([Download from Google Drive](https://drive.google.com/file/d/1Npp0kykITJp_nHdoKb0izSOGRHtoLI5A/view))
- **Visual Studio Code (VS Code)** - Code editor with C/C++ extension ([Download VS Code](https://code.visualstudio.com/))
- **Embedded C** - Programming language (C with embedded-specific features)
- **16-bit Microchip Microcontrollers** - PIC24 family CPUs
- **Development Boards** - Generation 1 (FTDI chip) or Generation 2 (Silicon Labs chip)

---

## Assessment Breakdown

| Assessment Component | Weight |
|---------------------|--------|
| Assignments          | 20%    |
| Quiz 1               | 20%    |
| Quiz 2               | 25%    |
| Quiz 3               | 35%    |
| **Total**            | **100%** |

### Quiz Structure

Each quiz consists of **two parts**:
1. **Paper-based (handwritten)** - Theoretical knowledge and core concepts
2. **Programming** - Practical coding and implementation tasks (students must use their own computer)

**Quiz Topics:**
- **Quiz 1:** Basic knowledge and basic programming (Foundations of Embedded Systems)
- **Quiz 2:** Embedded C programming and peripherals
- **Quiz 3:** Advanced embedded systems programming

---

## **Assignment Submission and Quiz Attendance Policy**

* Late submissions will be considered as not submitted.
* All quizzes will be conducted **onsite at CB40610(1)** according to the scheduled class date and time.
* If a student misses a quiz **without a valid reason**, they will receive **0 points** for that quiz.
* If a student misses a quiz **with a valid reason** (supported by an official leave form or evidence), they may request a make-up quiz and will receive **70% of the score earned** (actual score × 0.7).

---

## Course Progression

This course is structured in **three progressive phases**:

### Phase 1: Foundations (Weeks 1–4)
- Introduction to embedded systems and development environment
- Firmware development concepts and Embedded C fundamentals
- Event-driven programming (events, callbacks, timers, state machines, ADC)
- **Assessment:** Quiz 1 (Week 5) – 20%

### Phase 2: Embedded C Programming (Weeks 6–8)
- Advanced Embedded C techniques (standardized data types, pointers, memory management, `typedef`)
- Microcontroller peripherals programming (GPIO operations, register-level control)
- Hands-on applications (binary counter, floating point analysis, memory mapping)
- **Assessment:** Quiz 2 (Week 8) – 25%

### Phase 3: Advanced Techniques (Weeks 9–12)
- Program flow control and I/O manipulation (conditional statements, Sensor-Controller-Actuator model, Digital/Analog I/O, bit manipulation)
- Code optimization strategies (execution speed, memory/program length optimization, best practices)
- Advanced programming techniques (real-time timing, event-driven task scheduling, state machine architecture, modular peripheral control)
- **Assessment:** Quiz 3 (Week 13) – 35%

**Continuous Assessment:** Assignments throughout the semester – 20%

---

## Prerequisites & Requirements

To successfully participate in this course, students must have access to:

### Computer and Software Requirements
- **Computer** (Laptop or Desktop) with Windows (No Mac or Linux)
- **.NET 9.0** – Runtime required for TernionDevTools ([Download .NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0))
- **TernionDevTools (Teral Full Installer)** – Development toolchain including GCC XC16 compiler, libraries, and tools ([Download from Google Drive](https://drive.google.com/file/d/1Npp0kykITJp_nHdoKb0izSOGRHtoLI5A/view))
- **Visual Studio Code (VS Code)** – Code editor with C/C++ extension ([Download VS Code](https://code.visualstudio.com/))

### Hardware Requirements
- **Development Board** – Generation 1 (FTDI chip) or Generation 2 (Silicon Labs chip) microcontroller board
- **USB Cable** – For connecting development board to computer

### Knowledge & Skill Requirements
- **Programming Concepts** – Conditional statements, loops, functions, pointers, memory management
- **Hardware Interfacing** – Understanding of microcontroller peripherals (GPIO, timers, ADC, etc.)
- **Embedded C** – Programming language (C with embedded-specific features)

---

## Weekly Schedule Overview

| Week | Topic | Activities |
|------|-------|------------|
| 1 | Introduction to Embedded Systems and Development Environment | Learn & Practice |
| 2 | Development Environment Setup | Learn & Practice |
| 3 | Firmware Development and Embedded C Programming | Learn & Practice |
| 4 | Introduction to Event-Driven Programming | Learn & Practice |
| 5 | **Quiz 1** – Foundations of Embedded Systems | **Quiz 1 (20%)** |
| 6-7 | Embedded C Programming Fundamentals | Learn & Practice |
| 8 | **Quiz 2** – Embedded C Programming | **Quiz 2 (25%)** |
| 9-10 | Program Flow Control and I/O Manipulation | Learn & Practice |
| 11 | Programming Optimization Techniques | Learn & Practice |
| 12 | Advanced Programming Techniques | Learn & Practice |
| 13 | **Quiz 3** – Advanced Embedded Systems Programming | **Quiz 3 (35%)** |

Note: another 20% of the grade is from assignments.

For detailed weekly topics, see the [Course Outline](./Outline.md).

---

## Grading Scale

| Score Range | Grade |
|-------------|-------|
| 80 – 100    | A     |
| 75 – 79     | B+    |
| 70 – 74     | B     |
| 65 – 69     | C+    |
| 60 – 64     | C     |
| 55 – 59     | D+    |
| 50 – 54     | D     |
| 0 – 49      | F     |

---

## Quick Links

- [Course Syllabus](./Syllabus.md)
- [Detailed Course Outline](./Outline.md)
- [Week 1 Reading Material](./Week01/Week01-Read.md) | [Week 1 Self-Test Quiz](./Week01/Week01-Test.md)
- [Week 2 Reading Material](./Week02/Week02-Read.md) | [Week 2 Self-Test Quiz](./Week02/Week02-Test.md)
- [Week 3 Reading Material](./Week03/Week03-Read.md) | [Week 3 Self-Test Quiz](./Week03/Week03-Test.md)
- [Week 4 Reading (concepts)](./Week04/Week04-Read01.md) | [Week 4 Code](./Week04/Week04-Read02.md) | [Week 4 Test 1](./Week04/Week04-Test01.md) | [Week 4 Test 2](./Week04/Week04-Test02.md)
- [YouTube Playlist (EP01-EP20)](https://www.youtube.com/watch?v=R_Hrb4gQyqM&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj)
- [GitHub Repository](https://github.com/drsanti/INC342-2026)

---

**Last Updated:** 2026-01-13

---
