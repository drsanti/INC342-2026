# **Week 4 Self-Test Quiz (Code-Based)**

**Topic: EP8, EP9, EP10 — Code examples and key functions**  
**Based on:** Week04-Read02.md (code examples and key concepts)

---

## **Questions**

### **1. Short Answer**

In the basic blinking LED code (EP8), the line `interval(LED_On_Off, 500);` registers a periodic callback. What do the two arguments represent, and in what unit is the second argument?

---

### **2. Multiple Choice**

In the alternating-LED example (EP8), the code sets `gpio_set_level(GPIO_LED_NUM_0, GPIO_LEVEL_LOW);` before starting the interval. Why is this done?

A. To turn the LED off before blinking starts  
B. To set the initial state so LED 0 is ON and LED 3 is OFF, creating the alternating pattern  
C. To calibrate the GPIO pin  
D. To enable the interval timer  

---

### **3. True or False**

According to the key functions table (EP8), **Active Low** means that supplying Logic High (1) turns the board LED ON.

---

### **4. Short Answer**

What Ternion function binds a physical switch (e.g., Switch 3) to a callback function so that the callback runs whenever the switch has an event? Write the function name and its typical arguments.

---

### **5. Multiple Choice**

In the switch callback (EP9), the code uses `switch_t *psw = (switch_t *)param;`. Why is the variable named `psw` instead of `switch`?

A. `psw` is shorter and faster to type  
B. In C, `switch` is a reserved keyword and cannot be used as a variable name  
C. The Ternion library requires the name `psw`  
D. `switch` is the name of the hardware component  

---

### **6. Short Answer**

In the EP9 example, the condition `if (psw->state == SWITCH_STATE_ON)` is used inside the switch callback. What problem does this check solve, and what would happen without it?

---

### **7. True or False**

The switch callback function is invoked only when the user **presses** the button; it is not called when the button is released or held.

---

### **8. Multiple Choice**

In the ADC example (EP10), the raw sensor value is stored in a variable declared as `uint16_t adc_val;`. Why is a 16-bit unsigned type used for a 10-bit ADC result?

A. The ADC actually outputs 16-bit values  
B. 10-bit values (0–1023) fit within 16 bits; the extra bits allow safe storage and future use  
C. The Ternion library requires uint16_t for all analog reads  
D. To support negative voltage readings  

---

### **9. Short Answer**

In the EP10 source code, `serial_printf` is called with the format string `"Channel 1: %u (0x%04x)\r\n"`. What do the format specifiers `%u` and `%04x` mean, and why is the port (e.g., `SERIAL_NUM_1`) specified?

---

### **10. Multiple Choice**

According to Week04-Read02, when using a **Gen 1** board for the LDR (ADC) example, what must you do so that Analog Channel 1 is connected to the LDR?

A. Run `ternion select gen1`  
B. Set the jumper to the **right**  
C. Set the jumper to the **left**  
D. No change is needed; Gen 1 always uses the LDR on channel 1  

---

### **11. True or False**

In the EP10 demonstration described in the reading, covering the LDR sensor (making it darker) caused the ADC value to **increase** (e.g., from about 300 to about 800).

---

### **12. Scenario-Based Question**

A student implements the EP9 switch example but forgets to cast `param` and instead writes:

```c
void sw_callback(void *param) {
    if (param->state == SWITCH_STATE_ON) {
        gpio_toggle_level(GPIO_LED_NUM_2);
    }
}
```

Based on Week04-Read02:

1. Why will this code **not** compile (or why is it incorrect)?  
2. What single line should be added (and how should the `if` condition be written) to fix it?

---

## **Answers**

### **1.**

The first argument is the **callback function** (e.g., `LED_On_Off`) that runs each time the interval fires. The second argument is the **period in milliseconds** (e.g., 500 ms). So `interval(LED_On_Off, 500);` runs `LED_On_Off` every 500 ms.

---

### **2.**

**B.** To set the initial state so LED 0 is ON and LED 3 is OFF, creating the alternating pattern.

The board LEDs are **Active Low**: Logic Low turns them ON. Setting LED 0 to `GPIO_LEVEL_LOW` turns it ON; LED 3 is left High (OFF). When the interval toggles both, they alternate.

---

### **3.**

**False**

**Active Low** means **Logic Low (0)** turns the LED **ON**, and Logic High (1) turns it OFF. So supplying Logic High turns the LED OFF, not ON.

---

### **4.**

**`switch_set_callback(Switch_Num, Callback)`**

Example: `switch_set_callback(SWITCH_NUM_3, sw3_callback);` — This binds the physical Switch 3 to the function `sw3_callback`. Whenever Switch 3 generates an event (press, release, or hold), the callback is invoked.

---

### **5.**

**B.** In C, `switch` is a reserved keyword and cannot be used as a variable name.

The reading states: use a different variable name for the `switch_t *` pointer (e.g. `psw`, `evt`, `sw`).

---

### **6.**

The check ensures the LED toggles **only when the button is pressed** (STATE_ON), not when it is released or held. Without it, the callback would run on **press and release** (and hold), so `gpio_toggle_level` would run twice per press–release cycle and the LED would appear to toggle erratically or not change as expected.

---

### **7.**

**False**

The callback is invoked for **every** switch event: **press**, **release**, and **hold**. So the function runs when the button is pressed, when it is released, and when it is held. That is why filtering by `psw->state == SWITCH_STATE_ON` is needed to act only on press.

---

### **8.**

**B.** 10-bit values (0–1023) fit within 16 bits; the extra bits allow safe storage and future use.

A 10-bit ADC produces values 0–1023. A `uint16_t` can hold 0–65535, so it safely stores the result. The reading states that a 16-bit unsigned integer is used to store the value safely.

---

### **9.**

* **`%u`** — Unsigned integer in **decimal** (e.g., 512).  
* **`%04x`** — Unsigned integer in **hexadecimal** with **4 digits, zero-padded** (e.g., 0200).  

The **port** (e.g., `SERIAL_NUM_1`) is specified because `serial_printf` sends output to a **serial port**; unlike standard `printf`, you must choose which port (e.g., the one connected to the PC terminal).

---

### **10.**

**B.** Set the jumper to the **right**.

On Gen 1, Analog Channel 1 is shared. Moving the jumper to the **right** connects the channel to the LDR; moving it to the left connects it to the external port. Gen 2 has the LDR connected by default, so no jumper change is needed there.

---

### **11.**

**True**

The reading states that covering the LDR (darker) typically **increases** the value (e.g., ~300 → ~800), so you can infer light vs dark from the reading.

---

### **12.**

**1. Why it is incorrect:**  
`param` has type `void *`. The compiler does not know that it points to a struct with a `state` field, so `param->state` is invalid—you cannot access members through a `void *` without casting first.

**2. Fix:**  
Cast `param` to `switch_t *` and use a variable (e.g. `psw`) to access `state`:

```c
void sw_callback(void *param) {
    switch_t *psw = (switch_t *)param;
    if (psw->state == SWITCH_STATE_ON) {
        gpio_toggle_level(GPIO_LED_NUM_2);
    }
}
```

---

**Last Updated:** 2026-02-03

---
