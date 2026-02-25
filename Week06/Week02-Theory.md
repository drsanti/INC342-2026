**Name:** ________________________________ **Student ID:** ___________________ 

# INC342 Quiz 2 – Part 1 (Theory)

**Topic:** Week 6 (C Variables, Memory Architecture, and stdint.h)
**Time:** 45 Minutes | **Weight:** 15% of Course Score
**Instruction:** No electronic devices allowed.

---

## Questions

**1.** What is the primary reason embedded developers prefer using fixed-width types like **`uint8_t`** instead of traditional types like `unsigned char`? **(1 mark)**


**2.** In the current **16-bit architecture**, what is the byte size of an **`int`** versus a **`long`**? **(1 mark)**


**3.** How does the C compiler interpret a variable's value when used in a **boolean** context? Provide an example of a specific value that would be treated as "True". **(1 mark)**


**4.** Explain the concept of **Overflow** for an 8-bit unsigned integer. What is the numeric result of calculating $255 + 1$ in this context? **(1 mark)**


**5.** List the **three primary memory sections** used by the compiler and identify in which section **static variables** are stored. **(2 marks)**


**6.** What is a **round-off error** in floating point calculations, and why is it practically impossible to avoid in digital systems? **(1 mark)**


**7.** Which operator is used to retrieve the **memory address** of a variable, and what format specifier is commonly used with zero-padding to print a 4-digit hexadecimal address? **(1 mark)**


**8.** Define the purpose of the **`typedef`** keyword and explain how it improves code maintainability. **(1 mark)**


**9.** Calculate the numeric value represented by the macro **`UINT16_MAX`**. What hardware component (e.g., ADC resolution) is this value commonly associated with in a 16-bit system? **(1 mark)**


**10.** What is the concept of **Underflow**? If a `uint8_t` variable currently holds 0, what is the resulting value when you subtract 1 from it? **(1 mark)**


**11.** Which memory section is responsible for storing **local variables** created within a function, and what is its typical hexadecimal address range in the Ternion system? **(1 mark)**


**12.** Dynamic memory requested via the `malloc()` function is allocated from which memory section? **(1 mark)**


**13.** Why do many embedded compilers force both **`float`** and **`double`** types to occupy only **4 bytes** of memory? **(1 mark)**


**14.** To correctly print a 32-bit **Unsigned Long** counter via `serial_printf`, which format specifier should be used? **(1 mark)**


**15.** In the "4-bit LED Counter" application example, why do the LEDs physically show 0 ($0000_2$) when the software variable increments from 15 to 16? **(1 mark)**


**16.** What is the exact numeric range (Min to Max) of a signed 8-bit integer (**`int8_t`**)? **(1 mark)**


---

> **Important Note:** A solid understanding of the foundational concepts from **Weeks 1–5** is essential. Assessment questions may draw upon these prior topics, so students are strongly encouraged to review all previous reading materials.

---

**End of Part 1 (Theory)**

---

[**Back to Week 6 Index**](./README.md)

---

**Last Updated:** 2026-02-25

---
