# **Week 6 Reading Material: C Variables and Memory Management for Embedded Systems**

---

**YouTube Resources (EmbSysDev Playlist):**

| Topic | Link |
| :--- | :--- |
| **EP11** – Introduction to Variables | [Link](https://youtu.be/_hx1HK8BxpU?list=TLGGcrDYnFAk_VcyNTAyMjAyNg) |
| **EP12** – Variables and Data Behavior | [Link](https://youtu.be/meRtsUdHf_A?list=TLGG_5bVexQ5YocyNTAyMjAyNg) |
| **EP13** – Variable Size and Memory | [Link](https://youtu.be/ph2o_6RLHww?list=TLGGeZVEXdnyp7cyNTAyMjAyNg) |
| **EP14** – Variable Addresses and Sections | [Link](https://youtu.be/w2TuLlsNU38?list=TLGGYlCB6cxz8pYyNTAyMjAyNg) |
| **EP15** – Modern Variable Declaration | [Link](https://youtu.be/yjNE5GKyfSo?list=TLGGx4-vhz-lfVcyNTAyMjAyNg) |

---

## 1. Fundamental C Variable Categories

In embedded systems, variables are not merely abstract placeholders; they are physical allocations in memory that represent hardware states, sensor readings, or control logic. We categorize these into three primary groups to ensure deterministic data handling:

*   **Integers:** Used for whole numbers. In C, variables are signed by default (storing both positive and negative values). The `unsigned` keyword is mandatory when a variable should only represent positive values (0 to Max).
*   **Real Numbers (Floating Point):** Represent decimal values. While `double` typically offers higher precision than `float`, many embedded compilers force both to 4 bytes to save memory.
*   **Booleans:** Used for logical state. Modern firmware utilizes `<stdbool.h>` to map `false` to 0 and `true` to 1. In C, any non-zero value (even -57) is interpreted as **True**.

### 1.1 Implementation Example

```c
// Standard declarations with explicit initialization
char v1 = 'A';              // Character notation (stored as ASCII 65)
unsigned char v2 = 0x05;     // Hexadecimal notation (8-bit unsigned)
int v3 = 1000;              // Standard signed integer
long v4 = 123456L;          // Long integer (explicitly signed)
float f1 = 0.123f;          // Single precision
double f2 = 456.789;        // Double precision (often 4 bytes in MCU compilers)

bool systemReady = true;    // Boolean logic
```

---

## 2. Data Behavior: Overflow and Underflow

Firmware reliability depends on understanding the physical limits of your "data containers." If you exceed the capacity of a variable, the system does not crash; it wraps around, which can lead to catastrophic logic failures.

### 2.1 The Container Analogy

Think of a variable as a fixed-size box. Once it is full, adding more causes an **Overflow**, where the value "spills over" and restarts from the minimum.

*   **Overflow Logic (uint8_t):** 255 + 1 $\rightarrow$ 0.
*   **Underflow Logic (uint8_t):** 0 - 1 $\rightarrow$ 255 (values wrap to the maximum).

### 2.2 Floating Point Pitfalls

Digital systems are discrete, meaning they can only approximate continuous real numbers. This leads to **Round-off Errors**. For example, multiplying $0.123456789$ by $1,000,000$ might yield $123456.789062$. The "062" is digital noise—a byproduct of binary approximation—and must be accounted for in precision-critical calculations.

---

## 3. Memory Size and the sizeof() Operator

An architect must always account for the physical footprint of data. In our current **Gen 2 / 16-bit architecture**, the memory sizes are as follows:

*   **bool / char:** 1 byte (8 bits)
*   **int:** 2 bytes (Note: 32-bit systems use 4 bytes).
*   **long / float / double:** 4 bytes (The compiler forces `double` to 4 bytes for resource efficiency).

### 3.1 Size Verification Snippet

```c
int myData = 50;
serial_printf(1, "Size of 'myData': %d bytes\n", sizeof(myData)); // Returns 2
serial_printf(1, "Size of 'float': %d bytes\n", sizeof(float));   // Returns 4
```

---

## 4. Memory Architecture: Addresses and Sections

Every byte in memory has a unique **Address**, similar to a room number in an apartment complex. Knowing where a variable lives is as important as knowing what it holds.

### 4.1 Memory Sections

To optimize performance, the compiler organizes memory into distinct sections:

| Section | Purpose | Typical Hex Address Range |
| :--- | :--- | :--- |
| **Data Section** | Global and Static variables. | 800 range (e.g., 0x0822) |
| **Heap** | Dynamic memory via `malloc()`. | C00 range (e.g., 0x0C40) |
| **Stack** | Local variables (created inside functions). | 2000 range (e.g., 0x2036) |

### 4.2 Address Printing and Formatting

We use the **Address-of operator (&)** to retrieve a variable's location. Embedded developers often use `%x` (hexadecimal) with **Zero Padding** (`%.4x`) for a consistent 4-digit display.

---

## 5. Modern Variable Declaration (<stdint.h>)

Relying on traditional types like `int` is a "code smell" because their sizes change between CPUs. To ensure portability, professional firmware uses **fixed-width types**:

| Traditional Type | Modern Fixed-Width Type | Bit-Width | Size (Bytes) |
| :--- | :--- | :--- | :--- |
| `signed char` | `int8_t` | 8-bit | 1 byte |
| `unsigned char` | `uint8_t` | 8-bit | 1 byte |
| `unsigned int` | `uint16_t` | 16-bit | 2 bytes |
| `unsigned long` | `uint32_t` | 32-bit | 4 bytes |

**Custom Portability with typedef:** Use `typedef` to create aliases that describe the data’s purpose (e.g., `typedef uint16_t SensorData_t;`).

---

## 6. Summary of Functions and Specifiers

### 6.1 Key Functions and Operators

| Function/Operator | Purpose | Usage Example |
| :--- | :--- | :--- |
| `sizeof(type/var)` | Returns the size in bytes. | `sizeof(int)` |
| `&variable` | Returns the memory address. | `&myVar` |
| `%p` or `%x` | Format specifiers for addresses. | `serial_printf(1, "%p", &v1)` |
| `typedef` | Creates a type alias. | `typedef int8_t Age_t;` |

### 6.2 Printf Format Specifiers

| Specifier | Data Type | Usage Context |
| :--- | :--- | :--- |
| `%d` | Signed Integer | General counting |
| `%u` | Unsigned Integer | Values that cannot be negative |
| `%lu` | Unsigned Long | 32-bit counters |
| `%f` | Floating Point | Sensor decimals |
| `%x` | Hexadecimal | Raw register or address viewing |

---

## 7. Practical Example: Memory Mapping and Overflow

This comprehensive example demonstrates how to find the address and size of variables and observe overflow behavior in real-time.

```c
#include "ternion.h"

// Global variable - stored in DATA SECTION
uint16_t globalVar = 100; 

void main() {
    ternion_init(NULL);

    // Local variable - stored on STACK
    uint8_t localVar = 5; 

    // 1. Check Sizes
    serial_printf(1, "Size of uint16_t: %d bytes\r\n", sizeof(uint16_t)); // Returns 2
    
    // 2. Check Addresses
    serial_printf(1, "Global Addr: 0x%.4x\r\n", &globalVar); // Data Section
    serial_printf(1, "Local Addr:  0x%.4x\r\n", &localVar);  // Stack

    // 3. Demonstrate Overflow
    uint8_t counter = 255;
    counter = counter + 1;
    serial_printf(1, "Overflow Result (255+1): %u\r\n", counter); // Returns 0

    ternion_start(NULL);
}
```

---

**Last Updated:** 2026-02-25

---

[**Back to Week 6 Index**](./README.md) | [**Back to Main README**](../README.md)
