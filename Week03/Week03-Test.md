# **Week 3 Self-Test Quiz**

**Topic: Firmware Development and Embedded C Programming**

---

## **Questions**

### **1. Short Answer**

What is **firmware**, and what are its key characteristics in embedded systems?

---

### **2. Multiple Choice**

The firmware development process follows a five-step workflow. Which of the following correctly lists all five steps in order?

A. Edit, Create, Build, Flash, Test
B. Create, Edit, Build, Flash, Test
C. Build, Create, Edit, Flash, Test
D. Create, Build, Edit, Flash, Test

---

### **3. True or False**

The firmware development workflow is **linear**—once you complete the Test stage, the process is finished and you never return to previous stages.

---

### **4. Short Answer**

What is the difference between **Program Memory (ROM/Flash)** and **RAM** in embedded systems? Explain their purposes and characteristics.

---

### **5. Multiple Choice**

Which of the following correctly describes the build/compile process stages?

A. Preprocessing → Compilation → Assembly → Linking
B. Compilation → Preprocessing → Linking → Assembly
C. Assembly → Preprocessing → Compilation → Linking
D. Linking → Compilation → Assembly → Preprocessing

---

### **6. Short Answer**

What is the purpose of the `main` function in an Embedded C program, and what must it return?

---

### **7. True or False**

Every Embedded C program can have multiple `main` functions, each serving a different purpose in the program.

---

### **8. Multiple Choice**

When you run `ternion create .` in a project directory, which folder is the **primary location** for your application source code?

A. `core/`
B. `app/main/`
C. `build/`
D. `config/`

---

### **9. Short Answer**

What are the two essential initialization functions that every Embedded C program for Ternion boards must call? Explain what each function does.

---

### **10. Multiple Choice**

What does the `ternion_start(NULL)` function do?

A. Initializes the CPU and system clocks
B. Starts the internal event loop and begins an infinite loop
C. Compiles the C code into machine code
D. Transfers the `.hex` file to program memory

---

### **11. True or False**

The `ternion code-hide` command is used to compile and build your project files.

---

### **12. Short Answer**

What is the purpose of `serial_printf`, and how do you use it to print both text and variable values? Provide examples.

---

### **13. Multiple Choice**

After successfully building your project, what information does the compiler provide in the system summary?

A. Only RAM usage
B. Only ROM usage
C. Both RAM usage and ROM usage
D. Only compilation errors

---

### **14. Short Answer**

List the steps involved in building, flashing, and monitoring firmware. What command is used for each step?

---

### **15. Scenario-Based Question**

A student is developing their first Embedded C program. They write the following code:

```c
#include <ternion.h>

int main(void) {
    ternion_init(NULL);
    serial_printf(SERIAL_NUM_1, "Hello World!\r\n");
    return 0;
}
```

When they run `ternion build`, the code compiles successfully. However, when they flash it to the board and monitor the output, they don't see the "Hello World!" message.

Based on the Week 3 reading material, explain:
1. What is missing from this program?
2. Why is the message not appearing?
3. What should be added to make the program work correctly?

---

## **Answers**

### **1.**

**Firmware** is the machine code (Hex Code) that a CPU understands—it is the instruction set for microcontroller task execution. Unlike software that runs on general-purpose computers, firmware is specifically designed to control hardware peripherals and execute tasks on embedded systems.

**Key Characteristics:**
* Stored in **Program Memory (ROM/Flash)**—non-volatile memory that retains code even when power is removed
* Executed directly by the CPU
* Optimized for specific hardware and real-time operation
* Limited by memory constraints (both program memory and RAM)

---

### **2.**

**B.** Create, Edit, Build, Flash, Test

The firmware development process follows this five-step workflow:
1. **Create:** Set up your project structure with necessary configuration files
2. **Edit:** Write or modify your Embedded C code using a code editor
3. **Build:** Compile your C code into machine code (Hex Code) that the CPU can execute
4. **Flash:** Transfer the compiled `.hex` file from your computer to the microcontroller's program memory
5. **Test:** Verify that the firmware works correctly on the hardware

---

### **3.**

**False**

The firmware development workflow is **iterative** and **non-linear**. When testing reveals errors or unexpected behavior, you return to the **Edit** stage, make changes, rebuild, reflash, and test again. This cycle continues until the desired functionality is achieved.

---

### **4.**

**Program Memory (ROM/Flash):**
* Stores the compiled firmware code (`.hex` file)
* **Non-volatile**—retains code even when power is removed
* Limited capacity—must be managed efficiently
* The build process generates a `.hex` file that is sent to program memory

**RAM (Random Access Memory):**
* Stores variables and runtime data
* **Volatile**—data is lost when power is removed
* Limited capacity—requires careful management
* Used for stack, heap, and data sections

**Key Difference:** Program Memory stores the firmware code permanently, while RAM stores temporary runtime data that is lost when power is removed.

---

### **5.**

**A.** Preprocessing → Compilation → Assembly → Linking

The build process translates high-level C code into machine-executable code through these stages:
1. **Preprocessing:** `#include` directives are processed, macros are expanded
2. **Compilation:** C code is translated into **Assembly language**
3. **Assembly:** Assembly code is converted into **Object files** (binary machine code)
4. **Linking:** Object files are linked together into a single binary machine code file (`.hex`)

---

### **6.**

The `main` function serves as the **entry point** where program execution begins in an Embedded C program. Every Embedded C program requires exactly **one `main` function**, and it must return an integer (`int`). The `main` function is where the program starts executing when the microcontroller begins running the firmware.

---

### **7.**

**False**

Every Embedded C program requires exactly **one `main` function**. The `main` function serves as the entry point where program execution begins. Having multiple `main` functions would cause compilation errors because the compiler wouldn't know which one to use as the program entry point.

---

### **8.**

**B.** `app/main/`

The `app/main/` folder is the **primary location** for your application source code. It contains `main.c`—your main program file. This is where you write your Embedded C code. The other folders serve different purposes:
* `core/` and `HAL/` contain system-level libraries and header files
* `build/` stores compiled binary and hex files
* `config/` holds configuration settings

---

### **9.**

The two essential initialization functions are:

**1. `ternion_init(NULL)`:**
* **Purpose:** Configures CPU modules and initializes hardware peripherals
* **What it does:**
  * Initializes the CPU and system clocks
  * Configures timers, ADC, and other peripherals
  * Sets up hardware like LEDs and switches

**2. `ternion_start(NULL)`:**
* **Purpose:** Starts the internal event loop
* **What it does:**
  * Begins an **infinite loop** that continuously processes events
  * Enables event-driven programming capabilities
  * Keeps the program running and responsive to hardware events

**Important:** Both functions must be called in your `main` function for the board to function correctly.

---

### **10.**

**B.** Starts the internal event loop and begins an infinite loop

The `ternion_start(NULL)` function starts the internal event loop, which begins an infinite loop that continuously processes events. This enables event-driven programming capabilities and keeps the program running and responsive to hardware events. The code after `ternion_start(NULL)` will never execute because it is an infinite loop.

---

### **11.**

**False**

The `ternion code-hide` command is used to **hide system-level folders** in VS Code, helping you focus on your application code (`app/main/main.c`) without visual clutter. It does not compile or build your project. To build your project, you use the `ternion build` command.

---

### **12.**

`serial_printf` is used to send text and data from the microcontroller to your computer via serial communication. It allows you to display debug messages, variable values, and status information in the serial monitor.

**Printing Text:**
```c
serial_printf(SERIAL_NUM_1, "Hello World!\r\n");
```
* `SERIAL_NUM_1` specifies Serial Port 1
* `\r\n` adds a carriage return and newline (like pressing Enter)

**Printing Variables:**
```c
int value = 42;
serial_printf(SERIAL_NUM_1, "Value: %d\r\n", value);
```
* `%d` is the format specifier for integers
* The variable value is passed as an additional argument after the format string

---

### **13.**

**C.** Both RAM usage and ROM usage

After successfully building your project, the compiler provides a system summary showing:
* **RAM usage**—how much runtime memory is being used
* **ROM usage**—how much program memory is being used

Monitoring these values helps optimize code and avoid memory overflow. It's important to ensure you're not exceeding memory limits.

---

### **14.**

The steps for building, flashing, and monitoring firmware are:

**1. Build the Project:**
* Command: `ternion build`
* Purpose: Compiles your C code into machine code (`.hex` file)
* Check for errors in the output and fix any compilation issues

**2. Flash the Firmware:**
* Command: `ternion flash`
* Purpose: Transfers the compiled `.hex` file from your computer to the microcontroller's program memory
* Troubleshooting: Ensure USB is connected, drivers are installed, and board is powered

**3. Monitor Output:**
* Command: `ternion monitor`
* Purpose: Opens a serial communication window to view messages sent via `serial_printf` and system status updates
* To Exit: Press `Ctrl+C`

**Note:** Always save your code (`Ctrl + S`) before building.

---

### **15.**

**1. What is missing from this program?**

The program is missing the `ternion_start(NULL)` function call. While `ternion_init(NULL)` initializes the hardware, `ternion_start(NULL)` is required to start the internal event loop that keeps the program running.

**2. Why is the message not appearing?**

The message is not appearing because:
* The `ternion_start(NULL)` function is missing, so the event loop never starts
* The program reaches `return 0;` and exits immediately
* Without the event loop running, the serial communication and other system functions don't operate properly
* Even if `serial_printf` were called, the program would exit before the message could be sent

**3. What should be added to make the program work correctly?**

The program should be modified to include `ternion_start(NULL)`:

```c
#include <ternion.h>

int main(void) {
    ternion_init(NULL);
    ternion_start(NULL);  // This starts the event loop
    
    // This code will never execute (ternion_start is infinite loop)
    serial_printf(SERIAL_NUM_1, "Hello World!\r\n");
    return 0;
}
```

**Note:** The `serial_printf` call should ideally be placed before `ternion_start(NULL)` if you want to see it immediately, or it should be called from within a callback function (which will be covered in later weeks). However, with `ternion_start(NULL)` present, the event loop will run and the system will be functional.

---

**Last Updated:** 2026-01-13

---
