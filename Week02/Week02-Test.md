# **Week 2 Self-Test Quiz**

**Topic: Development Environment Setup**

---

## **Questions**

### **1. Short Answer**

List the **five stages** of the firmware development workflow in order, and explain why this workflow is considered iterative.

---

### **2. Multiple Choice**

Which of the following best describes why Command Line Interfaces (CLI) are emphasized in modern embedded systems development?

A. CLI tools are easier to use than graphical interfaces
B. CLI provides direct control, enables automation, integrates with code editors, and offers professional workflows
C. CLI tools are only available for Windows operating systems
D. CLI tools are required because graphical interfaces don't work with microcontrollers

---

### **3. True or False**

TernionDevTools CLI supports Windows, Mac, and Linux operating systems.

---

### **4. Short Answer**

What is included in the **TernionDevTools (Teral Full Installer)** package, and why is it described as an "all-in-one" development package?

---

### **5. Multiple Choice**

What is the **critical prerequisite** that must be installed BEFORE installing TernionDevTools?

A. Visual Studio Code
B. .NET 9.0 runtime
C. GCC XC16 compiler
D. FTDI drivers

---

### **6. Short Answer**

Why is it important to run the TernionDevTools installer as Administrator, and what can happen if you don't?

---

### **7. True or False**

After installing TernionDevTools, you must run `ternion install` to add Ternion commands to your system PATH.

---

### **8. Multiple Choice**

Which VS Code extension is **required** for Embedded C programming in this course?

A. Python extension
B. C/C++ Extension by Microsoft
C. Arduino extension
D. Embedded Systems extension

---

### **9. Short Answer**

What are the driver requirements for **Generation 1** and **Generation 2** development boards? Where can these drivers be downloaded if Windows doesn't automatically install them?

---

### **10. Multiple Choice**

What command is used to list all active COM ports to identify your development board?

A. `ternion list`
B. `ternion lsport`
C. `ternion ports`
D. `ternion show-com`

---

### **11. True or False**

The `ternion restart` command sends a reset signal to the microcontroller, causing the CPU to restart and begin executing firmware from the beginning.

---

### **12. Short Answer**

What is the purpose of the `ternion monitor` command, and what message should appear in the monitor window when you press the physical Reset button on your development board?

---

### **13. Multiple Choice**

What are the two methods available for performing a hardware reset during development?

A. Software reset using `ternion restart` and physical reset using the Reset button
B. Only software reset using `ternion restart`
C. Only physical reset using the Reset button
D. Power cycling and software reset

---

### **14. Short Answer**

Explain the benefits of using VS Code's integrated terminal for embedded systems development. How does it streamline the development workflow?

---

### **15. Scenario-Based Question**

A student has just installed TernionDevTools and connected their development board to their computer. They want to verify that their development environment is properly set up.

Based on the Week 2 reading material, explain:
1. What are the three essential commands they should use to test their setup?
2. What is the procedure for each command?
3. What should they observe to confirm everything is working correctly?
4. What is the final verification that confirms successful two-way communication?

---

## **Answers**

### **1.**

The five stages of the firmware development workflow are:

1. **Create:** Set up a new project with the necessary structure and configuration files
2. **Edit:** Write and modify firmware code using a code editor
3. **Build:** Compile the source code into machine code (Hex Code) that the microcontroller can execute
4. **Flash:** Transfer the compiled firmware to the microcontroller's program memory
5. **Test:** Verify that the firmware works correctly on the hardware

This workflow is considered **iterative** because you may return to the Edit stage multiple times based on testing results until the desired functionality is achieved. When testing reveals errors or unexpected behavior, you return to Edit, make changes, rebuild, reflash, and test again. This cycle continues until the desired functionality is achieved.

---

### **2.**

**B.** CLI provides direct control, enables automation, integrates with code editors, and offers professional workflows

Command Line Interfaces (CLI) are emphasized in modern embedded systems development because they:
* Provide direct control over development tools
* Enable automation and scripting
* Integrate seamlessly with code editors and terminals
* Offer a professional development workflow used in industry

Transitioning to a developer mindset means becoming comfortable with terminal/command prompt usage rather than relying solely on graphical user interfaces.

---

### **3.**

**False**

TernionDevTools CLI supports **Windows only** (no Mac or Linux support). This is an important limitation that students must be aware of when setting up their development environment.

---

### **4.**

**TernionDevTools (Teral Full Installer)** is an all-in-one development package that includes:

* **GCC XC16 compiler** – GCC-based compiler from Microchip for 16-bit PIC microcontrollers
* **Development libraries** – Pre-built libraries for common microcontroller functions
* **Command-line tools** – CLI utilities for building, flashing, and monitoring firmware
* **Documentation** – Reference materials and examples

It is described as "all-in-one" because a single installation provides everything needed for embedded systems development with 16-bit Microchip microcontrollers. You don't need to install the compiler, libraries, and tools separately—they all come in one package.

---

### **5.**

**B.** .NET 9.0 runtime

**.NET 9.0 runtime must be installed BEFORE installing TernionDevTools.** TernionDevTools requires .NET 9.0 to function, and the installation may fail if .NET 9.0 is not present. This is a critical prerequisite that must be completed first.

---

### **6.**

It is important to run the TernionDevTools installer as Administrator because:

* The software needs **elevated permissions** to access hardware components
* It needs to install **system-level components**
* Running as a standard user often causes **installation failures**

**What can happen if you don't:**
* The installation may fail
* System-level components may not be installed correctly
* The software may not have proper access to hardware components
* You may encounter "Access Denied" errors

**How to run as Administrator:**
* **Do NOT simply double-click** the installer file
* **Right-click** `ternion_full_installer.exe` and select **"Run as administrator"**

---

### **7.**

**True**

After installing TernionDevTools, you must open Command Prompt (as Administrator) and run the command: `ternion install`. This adds Ternion commands to your system PATH, allowing you to use `ternion` commands from any directory. Without this step, you won't be able to use `ternion` commands from the command line.

---

### **8.**

**B.** C/C++ Extension by Microsoft

The **C/C++ Extension by Microsoft** is **required** for Embedded C programming. It provides:
* Language support for Embedded C programming
* Syntax highlighting
* IntelliSense
* Code navigation
* Debugging features

It can be installed from the Extensions marketplace in VS Code.

---

### **9.**

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

### **10.**

**B.** `ternion lsport`

The `ternion lsport` command lists all active COM ports to identify your development board.

**How to Identify Your Board:**
1. Run `ternion lsport` with the board connected
2. Note the COM ports listed
3. **Unplug the board** and run the command again
4. The port that **disappears** is your board's COM port identifier

**Expected Output:**
* A list of available COM ports (e.g., COM3, COM4, COM5)
* Your development board should appear in this list

---

### **11.**

**True**

The `ternion restart` command executes a hardware reset on the board's CPU via the reset pin. It:
* Sends a reset signal to the microcontroller
* Causes the CPU to restart and begin executing firmware from the beginning
* Verifies that you have control over the hardware

**Expected Behavior:**
* The board should reset (you may see LEDs briefly change state)
* No error messages should appear

---

### **12.**

The `ternion monitor` command opens a serial communication window for two-way communication with the board.

**Purpose:**
* Allows you to receive data from the board (debug messages, sensor readings, status information)
* Allows you to send commands to the board (keyboard commands to control board behavior)
* Enables real-time interaction with your firmware

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

### **13.**

**A.** Software reset using `ternion restart` and physical reset using the Reset button

The hardware reset interface allows you to reboot the system during development using two methods:

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

### **14.**

VS Code's integrated terminal provides several benefits for embedded systems development:

**Benefits:**
* **Access terminal directly within VS Code** – No need to switch between applications
* **Run `ternion` commands without leaving the editor** – Execute build, flash, and monitor commands while viewing your code
* **View command output alongside your code** – See compilation errors, build summaries, and monitor output in the same window
* **Streamline the development workflow** – Everything is in one place

**Workflow Example:**
1. **Edit:** Write code in VS Code
2. **Build:** Run `ternion build` in integrated terminal
3. **Flash:** Run `ternion flash` in integrated terminal
4. **Monitor:** Run `ternion monitor` to view output
5. **Iterate:** Return to Edit based on results

This integration makes the development process more efficient and reduces context switching between different applications.

---

### **15.**

**1. Three Essential Commands:**

The three essential commands to test the development environment setup are:
* `ternion lsport` – List all active COM ports to identify the development board
* `ternion restart` – Execute a hardware reset on the board's CPU
* `ternion monitor` – Open a serial communication window for two-way communication

**2. Procedure for Each Command:**

**`ternion lsport`:**
* Run `ternion lsport` with the board connected
* Note the COM ports listed
* Unplug the board and run the command again
* The port that disappears is the board's COM port identifier

**`ternion restart`:**
* Run `ternion restart` in the terminal
* The board should reset (you may see LEDs briefly change state)
* No error messages should appear

**`ternion monitor`:**
* Run `ternion monitor` in the terminal
* A communication window should open
* Press the physical Reset button on the development board

**3. What to Observe:**

**For `ternion lsport`:**
* A list of available COM ports (e.g., COM3, COM4, COM5)
* The development board should appear in this list
* The port should disappear when the board is unplugged

**For `ternion restart`:**
* The board should reset (LEDs may briefly change state)
* No error messages should appear
* This verifies control over the hardware

**For `ternion monitor`:**
* A serial communication window should open
* The window should be ready to receive and send data

**4. Final Verification:**

The **final verification** that confirms successful two-way communication is:
* When you press the physical Reset button while `ternion monitor` is running, you should see a message like **"Ternion API V 1.0.1"** appear in the monitor window
* This **"Ternion API" message** confirms that:
  * The board is properly connected
  * Drivers are correctly installed
  * Serial communication is working
  * The development environment is properly configured

This is the ultimate confirmation that everything is set up correctly and ready for firmware development.

---

**Last Updated:** 2026-01-13

---
