# **Week 2 Reading Material: Development Environment Setup**

---

**YouTube Resources:** EP3, EP4, EP5

---

## 1. Overview of Development Workflow for Embedded Systems

Embedded systems development requires a specific workflow that integrates hardware and software components. Understanding this workflow is essential for efficient development and debugging.

### 1.1 Development Workflow Stages

The typical embedded systems development process follows these stages:

1. **Create:** Set up a new project with the necessary structure and configuration files
2. **Edit:** Write and modify firmware code using a code editor
3. **Build:** Compile the source code into machine code (Hex Code) that the microcontroller can execute
4. **Flash:** Transfer the compiled firmware to the microcontroller's program memory
5. **Test:** Verify that the firmware works correctly on the hardware

This workflow is **iterative**—you may return to the Edit stage multiple times based on testing results until the desired functionality is achieved.

### 1.2 Developer Mindset: Command Line Interfaces (CLI)

Modern embedded systems development emphasizes the use of **Command Line Interfaces (CLI)** as the standard practice. **Note:** TernionDevTools CLI supports **Windows only** (no Mac or Linux support). This approach:

* Provides direct control over development tools
* Enables automation and scripting
* Integrates seamlessly with code editors and terminals
* Offers a professional development workflow used in industry

**Key Point:** Transitioning to a developer mindset means becoming comfortable with terminal/command prompt usage rather than relying solely on graphical user interfaces.

---

## 2. Installation and Configuration of Software Tools

### 2.1 TernionDevTools (Teral Full Installer)

**TernionDevTools** is an all-in-one development package that provides everything needed for embedded systems development with 16-bit Microchip microcontrollers.

#### 2.1.1 What's Included

* **GCC XC16 compiler** – GCC-based compiler from Microchip for 16-bit PIC microcontrollers
* **Development libraries** – Pre-built libraries for common microcontroller functions
* **Command-line tools** – CLI utilities for building, flashing, and monitoring firmware
* **Documentation** – Reference materials and examples

#### 2.1.2 Prerequisites

Before starting the installation, ensure you have the following:

* **Windows operating system** (Windows 11 recommended, Windows 10 minimum) – No Mac or Linux support
* **.NET 9.0 runtime** – Required for TernionDevTools to function ([Download .NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0))
* **Administrator access** – Required for installation and hardware access

#### 2.1.3 Installation Process

**⚠️ IMPORTANT: Install .NET 9.0 First**
* **.NET 9.0 runtime must be installed BEFORE installing TernionDevTools**
* Download and install .NET 9.0 from: [Download .NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)
* TernionDevTools requires .NET 9.0 to function, and the installation may fail if .NET 9.0 is not present

**Step 1: Download**
* Navigate to the project's GitHub repository: [INC342-2026](https://github.com/drsanti/INC342-2026)
* Access the **TernionDevTools (Teral Full Installer)** via the [Google Drive link](https://drive.google.com/file/d/1Npp0kykITJp_nHdoKb0izSOGRHtoLI5A/view)
* Download the installer package

**Step 2: Extract the Installer**
* Right-click the downloaded file and select **"Extract All"** (or use a tool like 7-Zip)
* Extract the installer into a folder on your computer

**Step 3: Run as Administrator (Critical!)**
* **Do NOT simply double-click** the installer file
* **Right-click** `ternion_full_installer.exe` and select **"Run as administrator"**
* **Why?** The software needs elevated permissions to access hardware components and install system-level components. Running as a standard user often causes installation failures.

**Step 4: Add Environment Paths**
* After installation, open Command Prompt (as Administrator)
* Run the command: `ternion install`
* This adds Ternion commands to your system PATH, allowing you to use `ternion` commands from any directory

**Step 5: Troubleshooting**
* If the installer window doesn't appear, you can run it manually via Command Prompt:
  1. Open CMD as **Administrator**
  2. Navigate to the installer directory or use the full path
  3. Run: `ternion_full_installer.exe`

---

### 2.2 Visual Studio Code (VS Code) Configuration

**Visual Studio Code (VS Code)** serves as the primary code editor for this course, providing a powerful and extensible development environment.

#### 2.2.1 Installation

**Download and Install:**
* Download VS Code from the official website: [Download VS Code](https://code.visualstudio.com/)
* During installation, **ensure you check the box "Add to PATH"**
* This allows you to call VS Code from any terminal window using the `code` command

**Troubleshooting:**
* If you encounter "Access Denied" errors, restart the installer by right-clicking and selecting **"Run as administrator"**

#### 2.2.2 Essential Extensions

**C/C++ Extension by Microsoft:**
* **Required** – Provides language support for Embedded C programming
* Includes syntax highlighting, IntelliSense, code navigation, and debugging features
* Install from the Extensions marketplace in VS Code

#### 2.2.3 Optional Customizations

**Themes:**
* **GitHub Dark** – Dark theme that reduces eye strain
* **Atom Dark** – Alternative dark theme option
* Install from the Extensions marketplace

**Icons:**
* **Material Icon Theme** – Helps visually distinguish between different file types in your project
* Makes project navigation easier and more intuitive

#### 2.2.4 Integration with Terminal

VS Code includes an integrated terminal that allows you to:
* Run CLI commands directly within the editor
* View command output alongside your code
* Execute `ternion` commands without switching applications

---

## 3. Hardware Development Board Setup

### 3.1 Physical Connection

**Step 1: Prepare Your Workspace**
* Place your development board on a safe, non-conductive surface
* Ensure the area is free of moisture, metal objects, or static electricity sources

**Step 2: Connect via USB**
* Connect the USB cable to your development board
* Connect the other end to your computer's USB port
* **At least one USB 2.0 port is required** for proper communication

**Step 3: Verify Power**
* **Check for Power LED** – A "Power LED" should light up immediately when connected
* This confirms the board is receiving power from your computer
* If the LED doesn't light up, check the USB connection and cable

### 3.2 Driver Installation

If your computer cannot recognize the development board, you may need to install drivers:

**Generation 1 Boards (FTDI chip):**
* Require **FTDI VCP (Virtual COM Port) drivers**
* Windows may automatically install these, but if not, download from [FTDI's official website](https://ftdichip.com/drivers/)

**Generation 2 Boards (Silicon Labs chip):**
* Require **Silicon Labs CP210x VCP drivers**
* Windows may automatically install these, but if not, download from [Silicon Labs' official website](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads)

**Verification:**
* After driver installation, the board should appear in Device Manager under "Ports (COM & LPT)"
* Note the COM port number (e.g., COM3, COM4) for use with development commands

---

## 4. Testing and Verification of Development Environment

After installing software and connecting hardware, you must verify that everything is working correctly. Use these three essential commands to test your setup.

### 4.1 Command: `ternion lsport`

**Purpose:** List all active COM ports to identify your development board

**Usage:**
```bash
ternion lsport
```

**How to Identify Your Board:**
1. Run `ternion lsport` with the board connected
2. Note the COM ports listed
3. **Unplug the board** and run the command again
4. The port that **disappears** is your board's COM port identifier

**Expected Output:**
* A list of available COM ports (e.g., COM3, COM4, COM5)
* Your development board should appear in this list

### 4.2 Command: `ternion restart`

**Purpose:** Execute a hardware reset on the board's CPU via the reset pin

**Usage:**
```bash
ternion restart
```

**What It Does:**
* Sends a reset signal to the microcontroller
* Causes the CPU to restart and begin executing firmware from the beginning
* Verifies that you have control over the hardware

**Expected Behavior:**
* The board should reset (you may see LEDs briefly change state)
* No error messages should appear

### 4.3 Command: `ternion monitor`

**Purpose:** Open a serial communication window for two-way communication with the board

**Usage:**
```bash
ternion monitor
```

**Testing Procedure:**
1. Run `ternion monitor` in your terminal
2. A communication window should open
3. **Press the physical Reset button** on your development board
4. You should see a message like **"Ternion API V 1.0.1"** appear in the monitor window

**Expected Output:**
* Serial communication window displaying messages from the board
* **"Ternion API" message** confirms successful two-way communication
* This is the **final verification** that your development environment is properly configured

**To Exit:**
* Press `Ctrl+C` to close the monitor

---

## 5. Introduction to Debugging Tools and Hardware Interfaces

### 5.1 Serial Monitor

The **Serial Monitor** (accessed via `ternion monitor`) is a crucial debugging tool that allows you to:

**Receive Data from Board:**
* View debug messages, sensor readings, and status information
* Monitor program execution and variable values
* Identify runtime errors and unexpected behavior

**Send Commands to Board:**
* Send keyboard commands to control board behavior
* Trigger specific functions or test different modes
* Interact with your firmware in real-time

**Use Cases:**
* Debugging program logic and flow
* Verifying sensor readings and calculations
* Testing communication protocols
* Monitoring system performance

### 5.2 Hardware Reset Interface

The **hardware reset interface** allows you to reboot the system during development:

**Methods:**
* **Software reset:** Using `ternion restart` command
* **Physical reset:** Pressing the Reset button on the development board

**When to Use:**
* After flashing new firmware
* When the system becomes unresponsive
* To restart program execution from the beginning
* During debugging to test initialization sequences

**Benefits:**
* Quick system restart without power cycling
* Reliable way to recover from errors
* Essential for iterative development and testing

---

## 6. Development Workflow Integration

### 6.1 Code Editor and Terminal Integration

Modern development practices integrate the code editor with the terminal:

**VS Code Integrated Terminal:**
* Access terminal directly within VS Code
* Run `ternion` commands without leaving the editor
* View command output alongside your code
* Streamline the development workflow

**Workflow Example:**
1. **Edit:** Write code in VS Code
2. **Build:** Run `ternion build` in integrated terminal
3. **Flash:** Run `ternion flash` in integrated terminal
4. **Monitor:** Run `ternion monitor` to view output
5. **Iterate:** Return to Edit based on results

### 6.2 Project Structure

Understanding project structure helps organize your work:

**Typical Project Layout:**
* **Source files** (`.c` files) – Your Embedded C code
* **Header files** (`.h` files) – Function declarations and definitions
* **Configuration files** – Project settings and build configurations
* **Build output** – Compiled `.hex` files ready for flashing

**Best Practices:**
* Keep code organized in logical folders
* Use meaningful file and function names
* Comment your code for clarity
* Maintain consistent coding style

---

## 7. Key Terms for Review

Before the next session, students should be familiar with the following terms:

* Command Line Interface (CLI)
* TernionDevTools
* GCC XC16 compiler
* Visual Studio Code (VS Code)
* COM port
* Serial communication
* Hardware reset
* Firmware flashing
* Build process
* Serial monitor
* Driver installation
* Environment PATH

---

# Next Week

## Week 3: Firmware Development and Embedded C Programming

### What We Will Cover

Next week, we will begin writing firmware programs using Embedded C. This is a **hands-on programming session** where you will create your first embedded system application.

**Topics to be covered:**
* Introduction to firmware development concepts
* Firmware definition and development workflow
* Embedded C programming fundamentals:
  * Basic syntax and structure
  * The `main` function
  * `#include` directives
  * Essential functions (`ternion_init()`, `ternion_start()`)
* Project creation and structure
* Building and compiling firmware
* Flashing firmware to the microcontroller
* Testing and debugging techniques
* Introduction to `serial_printf` for debugging

### What to Prepare

**Before attending the class, please prepare the following:**

1. **Ensure your development environment is fully set up:**
   * TernionDevTools installed and `ternion install` completed
   * VS Code installed with C/C++ extension
   * Development board connected and verified (tested with `ternion lsport`, `ternion restart`, `ternion monitor`)

2. **Review basic C programming concepts:**
   * Functions and function calls
   * Variables and data types
   * Basic syntax (semicolons, braces, parentheses)

3. **Familiarize yourself with:**
   * Using the terminal/command prompt
   * Navigating directories in the terminal
   * Basic file operations

4. **Bring your laptop** with:
   * Development board connected
   * VS Code ready to use
   * Terminal/command prompt accessible

**Note:** We will guide you through creating your first project step-by-step during the class. Make sure your development environment is working correctly before class begins.

---

## **Self-Assessment**

After reading this material, please review the key concepts covered in this week's reading material:

* Development workflow for embedded systems (Create, Edit, Build, Flash, Test)
* Command Line Interface (CLI) usage and developer mindset
* TernionDevTools installation and configuration
* VS Code setup and essential extensions
* Hardware board connection and driver installation
* Testing commands (`ternion lsport`, `ternion restart`, `ternion monitor`)
* Serial monitor and debugging tools

Consider how the development workflow differs from traditional software development and why CLI tools are essential for embedded systems programming.

---

**Last Updated:** 2026-01-13

---
