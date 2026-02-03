# **Course Outline – INC342: Embedded Systems and Applications**

---

**YouTube Playlist:** [EP1-EP20](https://www.youtube.com/watch?v=R_Hrb4gQyqM&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj)

---

## **Week 1: Introduction to Embedded Systems and Development Environment**

* **Course overview, objectives, and project-based learning format:**
  * Applying microcontrollers to real-world measurement, control, and automation applications.
  * Project-based "learning by doing" approach: start with a goal, then design hardware and software to achieve it.
  * No prior electronics or programming background required; starts from software installation and basic C programming.
* **Introduction to embedded systems and their applications:**
  * Application areas: general automation and Industrial Internet of Things (IIoT).
  * IoT concepts: enabling microcontrollers to exchange data with mobile phones or web browsers via the internet.
* **Fundamental concepts:**
  * Hardware vs. Software (Firmware): Integration of electronic circuits (hardware) and microcontroller programming (software).
  * System Design Process: From concept to schematics, PCB layout, and 3D modeling.
* **Overview of embedded system components and architecture:**
  * CPU and Modules: 16-bit Microchip CPUs with WiFi modules (ESP8266 Gen 1, ESP32 Gen 2).
  * Board Generations: Gen 1 (training boards with large LEDs/switches) vs. Gen 2 (compact design for AI, data processing, or motherboard plug-ins).
  * On-board Peripherals: LEDs, switches, analog sensors (LDR), and buzzers.
* **Development tools and learning resources:**
  * Software Tools: Teral Full Installer (includes GCC XC16 compiler, libraries, and tools).
  * PCB/3D Design: Open-source tools (KiCad for PCB design, FreeCAD for 3D modeling).
  * GitHub Repository: drsanti/embedded-system-development (source code, software, and documentation).
* **YouTube Resources:** EP1, EP2


---

## **Week 2: Development Environment Setup**

* **Overview of the development workflow for embedded systems:**
  * Transition to **developer mindset** using **Command Line Interfaces (CLI)** (standard practice across Windows, Mac, and Linux).
  * Integration of code editor with terminal for project creation, building, and flashing firmware.
* **Installation and configuration of required hardware and software tools:**
  * **TernionDevTools (Teral Full Installer):**
    * Downloaded from project's GitHub repository via Google Drive.
    * Must be **Run as Administrator** for proper hardware access.
    * **Add Environment Paths** via `ternion install` command to recognize Ternion commands globally.
  * **Integrated Development Environment (IDE) configuration:**
    * **Visual Studio Code (VS Code)** as primary code editor.
    * Essential extension: **C/C++ by Microsoft** for language support.
    * Optional: **Material Icon Theme** and color themes (GitHub Dark, Atom Dark).
  * **Hardware development boards and microcontroller setup:**
    * Connect **Generation 1 (FTDI chip)** or **Generation 2 (Silicon Labs chip)** boards via USB.
    * Verify **Power LED** to confirm board is receiving power.
    * **Driver Installation:** FTDI drivers (Gen 1) or Silicon Labs CP210x drivers (Gen 2) if OS doesn't auto-recognize.
* **Testing and verification of the development environment:**
  * **`ternion ls-port`**: List active COM ports to identify the development board.
  * **`ternion restart`**: Execute **hardware reset** via CPU reset pin to verify control.
  * **`ternion monitor`**: Final verification for two-way communication; successful setup displays **"Ternion API" message** from board.
* **Introduction to debugging tools and hardware interfaces:**
  * **Serial Monitor**: Receive data from board or send keyboard commands to control board behavior.
  * **Hardware reset interface**: Reboot system during development process.
* **YouTube Resources:** EP3, EP4, EP5

---

## **Week 3: Firmware Development and Embedded C Programming**

* **Introduction to firmware development concepts:**
  * **Firmware Definition:** Machine code (Hex Code) that a CPU understands; instruction set for microcontroller task execution.
  * **Development Workflow:** Five-step process: **Create** (project setup), **Edit** (coding), **Build** (compiling), **Flash** (transferring code), **Test** (verifying results).
  * **Iterative Process:** Non-linear development; return to **Edit** stage when testing reveals errors until desired outcome is achieved.
* **Embedded C programming fundamentals:**
  * **Embedded C Syntax:** Every program requires exactly one `main` function returning an integer. Use `#include` preprocessor directives to access libraries.
  * **Memory Management:** Build process generates `.hex` file sent to **Program Memory (ROM/Flash)**. System summaries show **RAM** and **ROM** usage after build.
  * **The Build/Compile Process:** High-level C code → **Assembly language** → **Object files** → linked into single binary machine code file.
* **Basic firmware structure and organization:**
  * **Project Directory Structure:**
    * `app/main`: Primary location for application source code (`main.c`).
    * `core` and `HAL` (Hardware Abstraction Layer): Libraries and header files for peripheral control.
    * `Build`: Storage for binary and hex files generated during compilation.
  * **Essential Functions:** `ternion_init()` configures CPU modules (timers, ADC, etc.); `ternion_start()` begins **Event Loop** (infinite loop).
  * **Workspace Management:** Use `ternion code-hide` to hide system-level folders in VS Code, focusing on application code only.
* **Hands-on: Developing simple firmware programs:**
  * **Project Initialization:** Use `ternion create .` to generate project structure in working directory.
  * **Debugging and Output:** Use `serial_printf` to send text and variable data (e.g., integers with `%d`) from microcontroller to computer terminal.
  * **Error Analysis:** Interpret compiler messages by identifying file names, line numbers, and error descriptions (e.g., "too few arguments").
  * **Flashing and Monitoring:** Execute `ternion flash` to upload code; `ternion monitor` to view two-way communication between computer and board.
* **YouTube Resources:** EP6, EP7

---

## **Week 4: Introduction to Event-Driven Programming**

* **Concepts of event-driven programming in embedded systems:**
  * **Definition of Events:** Occurrence (e.g., user pressing a switch) represented as a variable the program can manage.
  * **User-Generated Events:** Users create events through hardware interactions; microcontroller interprets via software.
  * **Periodic Operations:** Repetitive actions (e.g., blinking LED) executed at regular intervals.
* **Event handling and interrupt-driven programming:**
  * **Callback Functions:** Register functions (e.g., `switch_set_callback`) that system automatically executes when hardware event occurs.
  * **Intervals and Timers:** Use timers (e.g., Timer 0) to create "intervals" for periodic tasks, similar to `setInterval` in web development.
  * **Data Structures in Events:** Use pointers (`pointer to void`) to pass event data into callback functions.
  * **Pointer Casting:** "Unwrap" generic pointers by casting to specific data structures (e.g., `switch_t`) to access event details (state, ID).
* **State machines and event processing:**
  * **Event States:** Single hardware interaction (e.g., switch) can trigger multiple states: **on, off, hold, repeat**.
  * **Filtering Events:** Use logic to isolate specific states (e.g., only act when switch is "on") to prevent callback execution during both press and release phases.
  * **Logic Toggling:** Use `gpio_toggle_level` to flip peripheral state (e.g., LED) based on event trigger.
* **Analog-to-Digital Conversion (ADC) as an Input Event:**
  * **Basics of ADC:** Convert analog environmental signals (0–3.3V) into digital values (0–1023 for 10-bit resolution).
  * **Environmental Sensing:** Use **LDR (Light Dependent Resistor)** to trigger software responses based on ambient light levels.
  * **Signal Monitoring:** Periodically read "Raw Data" from sensors; use **Serial Monitor** to debug and analyze digital representation of analog inputs.
* **Hands-on: Implementing event-driven applications:**
  * **LED Blinking:** Create periodic event using timer to toggle LED every 500ms.
  * **Switch Control:** Program LED to toggle only when specific button (e.g., Switch 3) is pressed.
  * **Light Sensing:** Develop program to monitor and print LDR values to terminal, observing system reactions to darkness and light.
* **YouTube Resources:** EP8, EP9, EP10
* **Weekly materials:** [Week04-Read01](./Week04/Week04-Read01.md) (concepts), [Week04-Read02](./Week04/Week04-Read02.md) (code), [Week04-Test01](./Week04/Week04-Test01.md), [Week04-Test02](./Week04/Week04-Test02.md)

---

## **Week 5: Quiz 1 – Foundations of Embedded Systems**

* **Quiz 1: Basic Knowledge and Basic Programming**
  * **Paper-based (handwritten):**
    * Embedded system concepts: hardware vs. software (firmware), system design process, components and architecture.
    * Development environment: CLI usage, workflow, testing commands (`ternion ls-port`, `ternion restart`, `ternion monitor`).
    * Firmware development: definition, workflow (Create, Edit, Build, Flash, Test), build/compile process, project structure.
    * Embedded C fundamentals: syntax, memory management, essential functions (`ternion_init()`, `ternion_start()`).
    * Event-driven programming: events, callbacks, timers/intervals, state machines, ADC basics.
  * **Programming:**
    * Embedded C: basic syntax, `main` function, `#include` directives, `serial_printf` debugging.
    * Firmware development: project creation (`ternion create .`), compilation, flashing (`ternion flash`), monitoring (`ternion monitor`).
    * Event-driven applications: LED blinking with timers, switch control, callbacks, event state filtering.

---

## **Week 6-7: Embedded C Programming Fundamentals**

* **Advanced Embedded C programming techniques:**
  * **Standardized Data Types (`stdint.h`):** Use fixed-width types (`int8_t`, `uint16_t`, `int32_t`) instead of `int` or `long` (which vary across CPUs) for code portability and clarity.
  * **Pointers and Memory Addressing:**
    * Every variable has unique **address** (location) in memory, accessed via `&` operator.
    * Use **pointers** to manage data memory and interface with dynamic memory.
    * Format address output using **hexadecimal** (e.g., `%p` or `%x`) and **zero padding** (e.g., `.4x`) for professional debugging.
  * **Memory Management and Sections:**
    * **Data Section:** Stores global and static variables.
    * **Stack:** Stores local variables created within functions.
    * **Heap:** Used for dynamic memory allocation via `malloc` and `free`.
  * **Custom Types with `typedef`:** Create meaningful aliases for data types (e.g., `SensorData_t`) for improved code readability and maintainability.
  * **Data Integrity:** **Overflow** and **underflow**—exceeding variable's max/min capacity causes value to "wrap around" (e.g., 8-bit unsigned 255 becomes 0 when 1 is added).
* **Microcontroller peripherals programming:**
  * **GPIO (General Purpose Input/Output):**
    * Control hardware peripherals (e.g., LEDs) by writing variable data directly to registers.
    * Use API functions (e.g., `led_write_4`) to output binary values to physical components.
  * **Memory Constraints:** Embedded systems have limited RAM compared to general-purpose computers; carefully select variable sizes to optimize memory usage.
* **Hands-on: Developing comprehensive embedded C applications:**
  * **Size Verification:** Use `sizeof()` operator to check exact byte consumption of different data types on 16-bit CPU.
  * **Binary Counter Implementation:** Develop program where variable acts as counter; binary state reflected in real-time on board's LEDs.
  * **Floating Point Analysis:** Test precision of `float` and `double` types; identify **round-off errors** during complex mathematical operations in digital systems.
  * **Memory Mapping:** Trace physical location of variables to confirm placement in Data, Stack, or Heap sections of RAM.
* **YouTube Resources:** EP11, EP12, EP13, EP14, EP15


---

## **Week 8: Quiz 2 – Embedded C Programming**

* **Quiz 2: Embedded C Programming and Peripherals**
  * **Paper-based (handwritten):**
    * Advanced Embedded C: standardized data types (`stdint.h`), fixed-width types (`int8_t`, `uint16_t`, `int32_t`), code portability.
    * Pointers and memory: variable addresses (`&` operator), pointer usage, hexadecimal formatting (`%p`, `%x`), zero padding.
    * Memory management: Data Section (global/static variables), Stack (local variables), Heap (`malloc`/`free`).
    * Custom types: `typedef` for code readability and maintainability.
    * Data integrity: overflow and underflow, value wrapping behavior.
    * Microcontroller peripherals: GPIO operations, register-level control, API functions (`led_write_4`), memory constraints.
  * **Programming:**
    * Embedded C programming: fixed-width data types, pointer operations, memory addressing, `typedef` usage.
    * Memory management: `sizeof()` operator, memory section placement (Data, Stack, Heap).
    * Peripheral control: GPIO operations, binary value output to hardware components.
    * Applications: binary counter implementation, floating point precision analysis, memory mapping verification.

---

## **Week 9-10: Program Flow Control and I/O Manipulation**

* **Program flow control in embedded systems:**
  * **Conditional statements:** Use `if` structures to detect specific hardware states (e.g., check if switch is in `switch_state_on` position before executing action).
  * **State Analysis:** Use timing diagrams and generic signals (High/Low) to design logic before coding; ensure program responds correctly to trigger points like "rising edge" of signal.
  * **Control flow optimization:** Transition from inefficient "brute force" methods (e.g., 16 separate `if/else` blocks for 4-bit display) to bitwise logic that reduces code length and improves execution speed.
  * **Logic Toggling:** Implement toggle logic where current state is read and inverted (ON to OFF, or OFF to ON) upon specific event.
* **I/O manipulation techniques:**
  * **The Sensor-Controller-Actuator Model:** Data flow: sensor measures physical parameters → controller (MCU) processes data → actuator (LED or motor) performs mechanical or light-based work.
  * **Digital I/O operations:**
    * Manage **Active High vs. Active Low** configurations; in Active Low system, sending Logic 0 (low) turns LED on.
    * Use `gpio_set_level` and `gpio_toggle_level` to interact directly with hardware pins.
  * **Analog I/O and ADC:** Use internal **Analog-to-Digital Converter (ADC)** to transform continuous environmental signals into digital data MCU can process.
  * **Bit Manipulation:** Use **Bitwise AND (`&`)** operator and "masking" techniques to isolate specific bits in variable to control individual LEDs (e.g., mask with `0x01` for bit 0 or `0x08` for bit 3).
  * **Binary Representation:** Output numerical data as 4-bit binary pattern to group of LEDs using utility functions like `LED_Write_4`.
* **Hands-on: Implementing I/O control applications:**
  * **Switch-Triggered Toggle:** Design system where pressing button once turns LED on; pressing again turns it off.
  * **4-bit Binary Counter:** Create program that increments `uint8_t` variable on every button press; display result in binary on four LEDs (0-15) and handle **overflow** (255 wraps back to 0).
  * **Custom LED Controller:** Write manual function to map variable bits to specific GPIO pins, replacing pre-built library functions with custom logic.
  * **Serial Debugging:** Use `serial_printf` to monitor counter values in Decimal, Hexadecimal, and Binary formats via terminal.
* **YouTube Resources:** EP16, EP17, EP18


---

## **Week 11: Programming Optimization Techniques**

* **Code optimization strategies for embedded systems:**
  * **Execution speed optimization:**
    * **Reducing Function Overhead:** Minimize function call frequency; function calls consume CPU resources.
    * **Register-Level Storage:** Use **`register` keyword** to suggest compiler store variables (loop counters, pointers) in CPU registers rather than RAM; CPU-to-register communication is faster than CPU-to-RAM.
    * **Bit Manipulation:** Replace lookup tables or repetitive logic with **Bit Shifting** (e.g., `<< 1`) to dynamically generate masks for I/O control.
  * **Memory and Program Length Optimization:**
    * **Ternary Operators:** Replace multi-line `if/else` blocks with ternary expressions (`condition ? value_if_true : value_if_false`) to shorten source code.
    * **Consolidating Logic:** Reduce redundant code by defining default states (e.g., set LED to "High" by default, only check "Low" condition) to eliminate unnecessary `else` branches.
    * **Eliminating Intermediate Variables:** Pass calculation results directly into functions instead of storing in temporary variables to save memory.
    * **Loop Consolidation:** Use `for` loops with arrays of pins or masks to replace repetitive, hard-coded operations for multiple hardware components.
* **Best practices for efficient embedded programming:**
  * **Naming Conventions:** Avoid special characters and spaces in folder and file names to prevent compiler errors with tools like GCC.
  * **Strategic Use of AI:** Use AI code completion only when developer fully understands underlying logic; otherwise, manual typing recommended for deeper learning.
  * **Readability vs. Conciseness:** While shortening code is optimization objective, maintain clarity so code remains "readable" and "parsable" by others.
  * **Parameter Management:** In resource-constrained systems, accessing **Global Variables** directly can be more efficient than parameter-passing overhead.
* **Hands-on: Optimizing embedded applications:**
  * **Refactoring LED Logic:** Transform "brute force" LED controller (separate blocks for each pin) into single optimized `for` loop iterating through 4-bit binary values.
  * **Dynamic Masking:** Implement system using bit-shifting within loop to control consecutive LEDs without hard-coded constants.
  * **Application Testing:** Verify optimized code preserves original functionality (e.g., 4-bit switch-triggered counter) through hardware flashing and terminal monitoring.
* **YouTube Resources:** EP19


---

## **Week 12: Advanced Programming Techniques**

* **Advanced programming techniques for embedded systems:**
  * **Real-time timing and interval management:** Use hardware **Timers** to create precise "intervals" for periodic tasks (e.g., shifting LED positions every 0.25 to 1 second).
  * **Event-driven task scheduling:** Coordinate asynchronous user inputs (switch presses via **callbacks**) with synchronous background tasks (timer-driven LED updates).
  * **Modular Peripheral Control:** Decouple hardware-specific code by creating independent `LEDController` function that accepts parameters; displays any 8-bit data regardless of source logic.
* **Software design patterns for embedded systems:**
  * **State Machine Architecture:** Manage complex application behavior by defining specific **modes** (Right, Left, Toggle, Pause) using `#define` constants and state variable to track current system behavior.
  * **Conditional Logic Optimization:** Use **ternary operator** (`condition ? true : false`) to replace multi-line `if-else` blocks for more concise, maintainable code.
  * **Resource Management (Early Return):** Implement `return` statements within periodic tasks to exit early if no data changed; prevents unnecessary hardware writes and **saves CPU energy**.
* **Hands-on: Developing advanced embedded applications:**
  * **Multi-Mode LED Controller:** System where four switches control unique behaviors:
    * **Switch 0/1:** Changes direction of "running" LED (Shift Right or Shift Left).
    * **Switch 2:** Toggles all LEDs on and off simultaneously.
    * **Switch 3:** Pauses current state of LEDs.
  * **Advanced Bitwise Manipulation:** Use bit-shifting operators (`<<` and `>>`) to move light patterns; apply **bitmasks** (`& 0x0F`) to ensure logic only affects targeted 4-bit hardware interface.
  * **Transition Logic Handling:** Write "reset" logic to ensure when switching from multi-LED mode (Toggle) to single-LED mode (Shift), system clears previous state for clean visual transition.
* **YouTube Resources:** EP20


---

## **Week 13: Quiz 3 – Advanced Embedded Systems Programming**

* **Quiz 3: Advanced Embedded Systems Development**
  * **Paper-based (handwritten):**
    * Program flow control: conditional statements (`if` structures), state analysis (timing diagrams, signal triggers), control flow optimization (bitwise logic vs. brute force), logic toggling.
    * I/O manipulation: Sensor-Controller-Actuator model, Active High vs. Active Low configurations, Digital I/O (`gpio_set_level`, `gpio_toggle_level`), Analog I/O and ADC, bit manipulation (masking with `&` operator), binary representation.
    * Code optimization: execution speed (function overhead, `register` keyword, bit shifting), memory/program length (ternary operators, logic consolidation, eliminating intermediate variables, loop consolidation), best practices (naming conventions, readability vs. conciseness, parameter management).
    * Advanced techniques: real-time timing (hardware timers, intervals), event-driven task scheduling (callbacks, synchronous/asynchronous coordination), modular peripheral control, state machine architecture (`#define` constants, mode tracking), resource management (early return, CPU energy saving).
  * **Programming:**
    * Program flow control: conditional logic implementation, state analysis and timing, bitwise operations for optimization, toggle logic.
    * I/O applications: switch-triggered toggle, 4-bit binary counter with overflow handling, custom LED controller, serial debugging (Decimal, Hexadecimal, Binary formats).
    * Code optimization: refactoring LED logic (brute force to optimized loops), dynamic masking with bit-shifting, application testing and verification.
    * Advanced applications: multi-mode LED controller (shift directions, toggle, pause), advanced bitwise manipulation (`<<`, `>>`, bitmasks), transition logic handling between modes.

---

## **Course Progression Summary**

This course is structured in three progressive phases, each building upon previous knowledge and culminating in a comprehensive assessment.

### **Phase 1: Foundations** (Weeks 1–4)
* **Learning Focus:** Introduction to embedded systems, development environment setup, firmware development, and event-driven programming
* **Key Topics:**
  * Embedded system concepts: hardware vs. software (firmware), system design process, components and architecture (16-bit Microchip CPUs, WiFi modules, board generations)
  * Development environment: CLI usage, TernionDevTools setup, IDE configuration (VS Code), hardware board setup, testing commands (`ternion ls-port`, `ternion restart`, `ternion monitor`)
  * Firmware development: development workflow (Create, Edit, Build, Flash, Test), build/compile process, project structure, essential functions (`ternion_init()`, `ternion_start()`)
  * Embedded C fundamentals: syntax, `main` function, memory management, `serial_printf` debugging
  * Event-driven programming: events, callback functions, timers/intervals, state machines, ADC basics, environmental sensing (LDR)
* **Assessment:** **Quiz 1** (Week 5) – 20% of final grade

### **Phase 2: Embedded C Programming** (Weeks 6–8)
* **Learning Focus:** Advanced Embedded C programming techniques and microcontroller peripheral control
* **Key Topics:**
  * Advanced Embedded C: standardized data types (`stdint.h`, fixed-width types), pointers and memory addressing, memory management (Data Section, Stack, Heap), `typedef` for custom types, data integrity (overflow/underflow)
  * Microcontroller peripherals: GPIO operations, register-level control, API functions (`led_write_4`), memory constraints
  * Hands-on applications: `sizeof()` operator, binary counter implementation, floating point analysis, memory mapping
* **Assessment:** **Quiz 2** (Week 8) – 25% of final grade

### **Phase 3: Advanced Techniques** (Weeks 9–12)
* **Learning Focus:** Program flow control, I/O manipulation, code optimization, and advanced programming techniques
* **Key Topics:**
  * Program flow control: conditional statements, state analysis (timing diagrams), control flow optimization (bitwise logic), logic toggling
  * I/O manipulation: Sensor-Controller-Actuator model, Digital I/O (Active High/Low, `gpio_set_level`, `gpio_toggle_level`), Analog I/O and ADC, bit manipulation (masking), binary representation
  * Code optimization: execution speed (function overhead, `register` keyword, bit shifting), memory/program length (ternary operators, logic consolidation, loop consolidation), best practices (naming conventions, readability vs. conciseness, parameter management)
  * Advanced techniques: real-time timing (hardware timers, intervals), event-driven task scheduling (callbacks, synchronous/asynchronous coordination), state machine architecture, modular peripheral control, resource management (early return, CPU energy saving)
* **Assessment:** **Quiz 3** (Week 13) – 35% of final grade

**Continuous Assessment:** Assignments throughout the semester – 20% of final grade

---

**Last Updated:** 2026-01-13

---
