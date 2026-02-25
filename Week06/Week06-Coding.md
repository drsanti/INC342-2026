**Name:** ________________________________ **Student ID:** ___________________ 

# INC342 Quiz 2 – Part 2 (Coding)

**Topic:** Practical Embedded C, Memory Mapping, and Hardware I/O (Week 6)
**Time:** 60 Minutes | **Weight:** 10% of Course Score
**Instruction:** No human collaboration. AI and reference materials allowed.

---

**Task 1: 4-bit Binary Counter with Overflow Control (2 marks)**

Write a complete `main.c` program that implements the following:
1.  Initialize a **global** `uint8_t` variable named `counter` starting at 250.
2.  Use **`PSW0`** (Switch 0) to increment the counter and **`PSW1`** (Switch 1) to decrement it via **event callbacks**.
3.  Output the current value of the `counter` to the board's LEDs using the `led_write_4()` function.
4.  Every time the value changes, print the following to the Serial Monitor:
    *   The current **value** in Decimal.
    *   The **memory address** of the `counter` variable in Hexadecimal format.
5.  **Requirement:** Verify and demonstrate that the variable wraps around (Overflow/Underflow) when it exceeds 255 or goes below 0.

**Submit:** Copy the clean code of the `main.c` and submit it to the LEB2. 

---

**Task 2: ADC Data Analysis and Memory Sections (2 marks)**

Write a complete `main.c` program that demonstrates the difference between **Data Section** and **Stack** memory:
1.  Declare a **`static uint16_t`** variable named `maxVoltage` in the global scope (Data Section).
2.  Create a periodic **interval** (every 1 second) that:
    *   Reads the raw ADC value from **`ANALOG_NUM_1`** (LDR).
    *   Stores it in a **local** variable named `currentSample` (Stack).
    *   Updates `maxVoltage` if the current sample is higher than the previous maximum.
3.  Inside the interval callback, print:
    *   The **address** of `maxVoltage` (Data Section).
    *   The **address** of `currentSample` (Stack).
4.  Observe and describe in a comment if the addresses are in the 800-range or 2000-range.

**Submit:** Copy the clean code of the `main.c` and submit it to the LEB2. 

---

**Task 3: Custom Types and Precision Analysis (1 mark)**

Write a complete `main.c` program that uses **`typedef`** to create a custom type for sensor data:
1.  Define `typedef float LuxValue_t;`.
2.  Calculate the "Lux" by taking a raw ADC reading and multiplying it by a scaling factor (e.g., `0.322f`).
3.  Store the result in a variable of type `LuxValue_t`.
4.  Use the **`sizeof()`** operator to print the byte size of your custom `LuxValue_t` to the Serial Monitor.
5.  If the value is greater than 100.0, turn **`LED3`** ON; otherwise, turn it OFF.

**Submit:** Copy the clean code of the `main.c` and submit it to the LEB2. 

---

**End of Part 2 (Coding)**

---

[**Back to Week 6 Index**](./README.md)

---

**Last Updated:** 2026-02-25

---
