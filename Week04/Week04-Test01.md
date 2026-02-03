# **Week 4 Self-Test Quiz**

**Topic: Periodic Operations, Events, and Analog Sensors**

---

## **Questions**

### **1. Short Answer**

What is a **periodic operation** in the context of embedded systems? Give a real-world example mentioned in the learning material.

---

### **2. Multiple Choice**

If you want to compile your code and immediately transfer it to the board using a single command in the terminal, which "stacked" command should you use?

A. `ternion build_flash`
B. `ternion build flash`
C. `ternion compile upload`
D. `ternion start flash`

---

### **3. True or False**

When using a **Gen 2** board, you must manually run the command `ternion select gen2` because the system defaults to Gen 1 settings.

---

### **4. Short Answer**

Explain what the function `gpio_toggle_level` does to an LED.

---

### **5. Multiple Choice**

In the Ternion system, what is the correct logic level to turn an LED **ON** if the hardware is wired as **Active Low**?

A. Logic High (1)
B. Logic Low (0)
C. Logic Float
D. Logic 3.3V

---

### **6. Short Answer**

When writing a callback function for a switch (e.g., `switch_callback`), the function receives a `void *param`. What must you do to this parameter to access the switch's state?

---

### **7. True or False**

A switch callback function is only triggered when the button is **pressed**, not when it is **released**.

---

### **8. Multiple Choice**

The Ternion board uses a 10-bit Analog-to-Digital Converter (ADC). What is the range of digital values it can produce from an analog input (0 V to 3.3 V)?

A. 0 to 255
B. 0 to 1023
C. 0 to 4095
D. 0 to 100

---

### **9. Short Answer**

If you are using a **Gen 1** board and want to use the LDR (Light-Dependent Resistor) sensor, what physical configuration change must you make to the board?

---

### **10. Multiple Choice**

Which command creates a new project inside a specific folder named `ep09_switch` rather than in the current directory?

A. `ternion create .`
B. `ternion new ep09_switch`
C. `ternion create ep09_switch`
D. `ternion init ep09_switch`

---

### **11. True or False**

In the specific LDR circuit used in the video demonstration, covering the sensor (making it darker) caused the ADC value to **increase** (e.g., from 300 to 800).

---

### **12. Scenario-Based Question**

A student writes code to toggle an LED when a switch is pressed. They notice that the LED toggles erratically—sometimes turning on when pressed, sometimes turning off when released. They are using the following code inside their callback:

```c
void switch_callback(void *param) {
    gpio_toggle_level(GPIO_LED_NUM_0);
}
```

Based on the reading material:
1. Why is this erratic behavior happening?
2. What specific check needs to be added to the code to fix this?

---

## **Answers**

### **1.**

A **periodic operation** is an action or event that occurs repeatedly at specific time intervals. Real-world examples from the material include clapping hands to a rhythm, or in electronics, an LED blinking ON and OFF at a fixed interval.

---

### **2.**

**B.** `ternion build flash`

This is a **stacked command**. It runs the build process and, if successful, immediately flashes the firmware to the board.

---

### **3.**

**True**

The toolchain defaults to **Gen 1**. If you use a **Gen 2** board, you must run `ternion select gen2` so the library targets the correct hardware.

---

### **4.**

The `gpio_toggle_level` function changes the current state of a GPIO pin to the opposite. If the LED is **ON**, it turns **OFF**; if it is **OFF**, it turns **ON**.

---

### **5.**

**B.** Logic Low (0)

The board LEDs are wired **Active Low**. A Logic Low (0) turns the LED ON; Logic High (1) turns it OFF.

---

### **6.**

You must **cast** the `void *param` to a pointer of the correct type, such as `switch_t *`. For example: `switch_t *evt = (switch_t *)param;`. Then you can access fields like `evt->state`. (In C, you cannot use the variable name `switch` because it is a reserved keyword.)

---

### **7.**

**False**

The callback is invoked for **any** change in the switch state—press, release, or hold. Both press and release generate events, so the function runs for each.

---

### **8.**

**B.** 0 to 1023

A 10-bit ADC has 2^10 = 1024 possible values, so the range is 0 to 1023.

---

### **9.**

You must move the **jumper** to the **right** position. On Gen 1 boards, analog channel 1 is shared; moving the jumper to the right connects it to the LDR; moving it to the left connects it to the external port.

---

### **10.**

**C.** `ternion create ep09_switch`

Using a name after `create` creates a new folder with that name. Using `ternion create .` creates the project in the *current* directory.

---

### **11.**

**True**

In the demonstration, covering the sensor (blocking light) caused the ADC value to increase (e.g., from about 300 to 800).

---

### **12.**

**1. Why is this happening?**

The switch produces events for **both** press and release. Without filtering, `gpio_toggle_level` runs on press *and* on release, so the LED toggles twice and appears erratic.

**2. What needs to be added?**

Filter by the switch state: cast `param` to `switch_t *` (using a variable name other than `switch`, e.g. `evt`) and only toggle when the button is pressed:

```c
void switch_callback(void *param) {
    switch_t *evt = (switch_t *)param;
    if (evt->state == SWITCH_STATE_ON) {
        gpio_toggle_level(GPIO_LED_NUM_0);
    }
}
```

This way the LED toggles only on press, not on release.

---

**Last Updated:** 2026-02-03

---
