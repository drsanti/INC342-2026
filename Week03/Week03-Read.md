# **Week 3 Reading Material: Firmware Development and Embedded C Programming**

---

**YouTube Resources:** EP6, EP7

---

## 1. Introduction to Firmware Development Concepts

### 1.1 Firmware Definition

**Firmware** is the machine code (Hex Code) that a CPU understands—it is the instruction set for microcontroller task execution. Unlike software that runs on general-purpose computers, firmware is specifically designed to control hardware peripherals and execute tasks on embedded systems.

**Key Characteristics:**
* Stored in **Program Memory (ROM/Flash)**—non-volatile memory that retains code even when power is removed
* Executed directly by the CPU
* Optimized for specific hardware and real-time operation
* Limited by memory constraints (both program memory and RAM)

### 1.2 Development Workflow

The firmware development process follows a **five-step workflow**:

1. **Create:** Set up your project structure with necessary configuration files
2. **Edit:** Write or modify your Embedded C code using a code editor
3. **Build:** Compile your C code into machine code (Hex Code) that the CPU can execute
4. **Flash:** Transfer the compiled `.hex` file from your computer to the microcontroller's program memory
5. **Test:** Verify that the firmware works correctly on the hardware

**Important:** This workflow is **iterative** and **non-linear**. When testing reveals errors or unexpected behavior, you return to the **Edit** stage, make changes, rebuild, reflash, and test again. This cycle continues until the desired functionality is achieved.

---

## 2. Embedded C Programming Fundamentals

### 2.1 Embedded C Syntax

Embedded C follows standard C syntax with some embedded-specific considerations:

**The `main` Function:**
* Every Embedded C program requires exactly **one `main` function**
* The `main` function must return an integer (`int`)
* It serves as the entry point where program execution begins

**Basic Structure:**
```c
#include <ternion.h>

int main(void) {
    // Your code goes here
    return 0;
}
```

**Preprocessor Directives:**
* Use `#include` directives to access libraries and header files
* `#include <ternion.h>` provides access to Ternion library functions
* Header files contain function declarations and definitions needed for your program

### 2.2 Memory Management

Understanding memory usage is crucial in embedded systems development:

**Program Memory (ROM/Flash):**
* Stores the compiled firmware code (`.hex` file)
* Non-volatile—retains code when power is removed
* Limited capacity—must be managed efficiently
* The build process generates a `.hex` file that is sent to program memory

**RAM (Random Access Memory):**
* Stores variables and runtime data
* Volatile—data is lost when power is removed
* Limited capacity—requires careful management
* Used for stack, heap, and data sections

**System Summaries:**
* After building, the compiler provides summaries showing:
  * **RAM usage**—how much runtime memory is being used
  * **ROM usage**—how much program memory is being used
* Monitoring these values helps optimize code and avoid memory overflow

### 2.3 The Build/Compile Process

The build process translates high-level C code into machine-executable code:

**Compilation Stages:**
1. **Preprocessing:** `#include` directives are processed, macros are expanded
2. **Compilation:** C code is translated into **Assembly language**
3. **Assembly:** Assembly code is converted into **Object files** (binary machine code)
4. **Linking:** Object files are linked together into a single binary machine code file (`.hex`)

**Output:**
* The final `.hex` file contains the machine code that the microcontroller CPU can execute
* This file is what gets flashed to the program memory

---

## 3. Basic Firmware Structure and Organization

### 3.1 Project Directory Structure

When you create a new project using `ternion create .`, the following structure is generated:

**`app/main/`:**
* **Primary location** for your application source code
* Contains `main.c`—your main program file
* This is where you write your Embedded C code

**`core/` and `HAL/` (Hardware Abstraction Layer):**
* Contains **libraries and header files** for peripheral control
* Provides functions for GPIO, timers, ADC, and other hardware interfaces
* These are system-level files—typically you don't modify them directly

**`build/`:**
* Storage for **binary and hex files** generated during compilation
* Contains the compiled output ready for flashing

**`config/`:**
* Holds **configuration settings** for your project
* Project-specific settings and build configurations

**`.vscode/`:**
* Contains **editor settings** for VS Code
* Includes theme customizations and workspace configurations

### 3.2 Essential Functions

Every Embedded C program for Ternion boards requires two essential initialization functions:

**`ternion_init(NULL)`:**
* **Purpose:** Configures CPU modules and initializes hardware peripherals
* **What it does:**
  * Initializes the CPU and system clocks
  * Configures timers, ADC, and other peripherals
  * Sets up hardware like LEDs and switches
* **Parameter:** Currently uses `NULL` (we'll learn about callback functions later)

**`ternion_start(NULL)`:**
* **Purpose:** Starts the internal event loop
* **What it does:**
  * Begins an **infinite loop** that continuously processes events
  * Enables event-driven programming capabilities
  * Keeps the program running and responsive to hardware events
* **Parameter:** Currently uses `NULL` (callback functions will be introduced later)

**Important:** Both functions must be called in your `main` function for the board to function correctly.

### 3.3 Workspace Management

**Hiding System-Level Folders:**
* Use `ternion code-hide` command to hide system-level folders in VS Code
* This helps focus on your application code (`app/main/main.c`) without visual clutter
* Makes it easier to navigate and work with your project

**Best Practices:**
* Keep your application code organized in `app/main/`
* Don't modify files in `core/` or `HAL/` unless necessary
* Use meaningful file and function names
* Comment your code for clarity

---

## 4. Hands-On: Developing Simple Firmware Programs

### 4.1 Project Initialization

**Step 1: Create Project Directory**
* Create a main folder (e.g., on your Desktop) named **"Ternion"** or similar
* Inside that, create a subfolder for your specific project (e.g., **"ep06_hello_world"**)
* This subfolder is your **Project Directory**

**Step 2: Open in VS Code**
* Open **Visual Studio Code (VS Code)**
* Open your project folder using **File > Open Folder**
* Navigate to your project directory

**Step 3: Configure Terminal**
* Open the integrated terminal via **Terminal > New Terminal** or press `Ctrl + J`
* **Set the Default Profile:** Ensure you are using **Command Prompt (CMD)**
  * Click the arrow next to the "+" in the terminal
  * Select **"Set Default Profile"**
  * Choose **Command Prompt**

**Step 4: Generate Project Structure**
* In the terminal, navigate to your project directory
* Run the command: `ternion create .`
* The **dot (.)** tells the system to create project files in the current directory
* This generates the complete project structure (app, core, config, etc.)

### 4.2 Writing Your First Program

**Location:** Your source code is located in `app/main/main.c`

**Basic Program Structure:**
```c
#include <ternion.h>

int main(void) {
    // Initialize hardware
    ternion_init(NULL);
    
    // Start event loop
    ternion_start(NULL);
    
    // This code will never execute (ternion_start is infinite loop)
    return 0;
}
```

**Adding Output:**
* Use `serial_printf` to send text and data from the microcontroller to your computer
* Example:
```c
serial_printf(SERIAL_NUM_1, "Hello World!\r\n");
```
* `SERIAL_NUM_1` specifies Serial Port 1
* `\r\n` adds a carriage return and newline (like pressing Enter)

**Printing Variables:**
* Use format specifiers to print variable values
* Example for integers:
```c
int value = 42;
serial_printf(SERIAL_NUM_1, "Value: %d\r\n", value);
```
* `%d` is the format specifier for integers

### 4.3 Building and Compiling

**Step 1: Save Your Code**
* Press `Ctrl + S` to save your `main.c` file
* Always save before building

**Step 2: Build the Project**
* In the terminal, run: `ternion build`
* The compiler translates your C code into machine code
* **Check for Errors:**
  * If you see **red text**, there are compilation errors
  * Read the error message carefully—it includes:
    * **File name** where the error occurred
    * **Line number** where the error is located
    * **Error description** (e.g., "too few arguments", "undefined identifier")
  * Fix the errors and rebuild

**Step 3: Review Build Summary**
* After successful build, check the system summary
* Note **RAM usage** and **ROM usage** values
* Ensure you're not exceeding memory limits

### 4.4 Flashing and Monitoring

**Step 1: Flash the Firmware**
* Run: `ternion flash`
* This transfers the compiled `.hex` file to the microcontroller's program memory
* **Troubleshooting:**
  * If the computer can't find your board:
    * Ensure USB is plugged in
    * Check that correct drivers are installed
    * Verify board is powered (Power LED is on)
    * Run `ternion lsport` to check COM port

**Step 2: Monitor Output**
* Run: `ternion monitor`
* Opens a serial communication window
* You can see:
  * Messages sent via `serial_printf`
  * System status updates
  * Two-way communication between computer and board
* **To Exit:** Press `Ctrl+C`

**Step 3: Test and Iterate**
* Observe the results on your board and in the monitor
* If behavior is incorrect, return to **Edit** stage
* Make changes, rebuild, reflash, and test again

### 4.5 Error Analysis

**Understanding Compiler Messages:**
* Compiler errors provide valuable information:
  * **File name:** Which file has the error
  * **Line number:** Exact location of the problem
  * **Error description:** What went wrong

**Common Error Types:**
* **"too few arguments":** Function call missing required parameters
* **"undefined identifier":** Variable or function name not recognized
* **"syntax error":** Incorrect C syntax (missing semicolon, bracket, etc.)
* **"expected ';'":** Missing semicolon at end of statement

**Debugging Strategy:**
1. Read the error message carefully
2. Go to the specified file and line number
3. Check the code around that line
4. Fix the issue
5. Rebuild and verify the error is resolved

---

## 5. Key Terms for Review

Before the next session, students should be familiar with the following terms:

* Firmware
* Machine code / Hex Code
* Program Memory (ROM/Flash)
* RAM (Random Access Memory)
* Build process
* Compilation
* Assembly language
* Object files
* Linking
* `main` function
* `#include` directive
* `ternion_init()`
* `ternion_start()`
* Event loop
* `serial_printf`
* Format specifier
* Project structure
* Hardware Abstraction Layer (HAL)

---

# Next Week

## Week 4: Introduction to Event-Driven Programming

### What We Will Cover

Next week, we will explore **event-driven programming**—a fundamental paradigm for embedded systems that enables responsive and efficient firmware design.

**Topics to be covered:**
* Concepts of event-driven programming in embedded systems
* Definition of events and how they are represented
* Callback functions and event handling
* Timers and intervals for time-based events
* State machines for managing program flow
* Analog-to-Digital Conversion (ADC) basics
* Environmental sensing using LDR (Light Dependent Resistor)
* Event filtering and state management
* Hands-on: Creating event-driven applications (LED blinking, switch control)

### What to Prepare

**Before attending the class, please prepare the following:**

1. **Ensure you can successfully create, build, flash, and test a basic program:**
   * Create a project using `ternion create .`
   * Write a simple program with `ternion_init()` and `ternion_start()`
   * Build using `ternion build`
   * Flash using `ternion flash`
   * Monitor output using `ternion monitor`
   * Use `serial_printf` to display messages

2. **Review the concept of functions:**
   * Function definitions and calls
   * Function parameters
   * Return values

3. **Familiarize yourself with:**
   * Basic C syntax (semicolons, braces, parentheses)
   * Variable declarations
   * Basic data types (int, char)

4. **Bring your laptop** with:
   * Development board connected
   * VS Code with a working project
   * Terminal/command prompt ready

**Note:** We will build upon the basic firmware structure you learned this week. Make sure you're comfortable with the Create, Edit, Build, Flash, Test workflow before proceeding.

---

## **Self-Assessment**

After reading this material, please review the key concepts covered in this week's reading material:

* Firmware definition and development workflow (Create, Edit, Build, Flash, Test)
* Embedded C syntax and the `main` function
* Memory management (Program Memory vs. RAM)
* Build/compile process (C code → Assembly → Object files → Hex file)
* Project directory structure and organization
* Essential functions (`ternion_init()`, `ternion_start()`)
* Project creation using `ternion create .`
* Using `serial_printf` for debugging and output
* Building, flashing, and monitoring firmware
* Error analysis and debugging techniques

Consider how firmware development differs from traditional software development, particularly in terms of memory constraints, hardware interaction, and the iterative development cycle.

---

**Last Updated:** 2026-01-13

---
