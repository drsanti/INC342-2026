# Week 4 Code Examples: EP8, EP9, EP10

**Companion:** [Week04-Read01](Week04-Read01.md) (concepts) · **Self-test:** [Week04-Test02](Week04-Test02.md)

This document contains **C code and explanations** from the EmbSysDev video series for Week 4. Each section corresponds to one episode and includes runnable examples plus key functions and concepts.

**Video resources:**

| Episode | Topic | Link |
|---------|--------|------|
| **EP8** | Periodic operations & blinking LED | [YouTube](https://www.youtube.com/watch?v=vuMPcCpqx5k&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=8) |
| **EP9** | Switches and events | [YouTube](https://www.youtube.com/watch?v=Yul2FaMqmug&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=9) |
| **EP10** | Analog-to-digital converter (ADC) | [YouTube](https://www.youtube.com/watch?v=cqQ0Wxi7YEI&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=10) |

---

## 1. EP8: Periodic Operation and Blinking LED

**Video:** [EP8 – Blinking LED](https://www.youtube.com/watch?v=vuMPcCpqx5k&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=8)

### 1.1 Basic Blinking LED

Makes **LED 0** blink every 500 ms using a periodic **interval** (similar to `setInterval` in JavaScript).

```c
#include <ternion.h>

// Callback: runs every time the interval fires.
void LED_On_Off(void *p) {
    gpio_toggle_level(GPIO_LED_NUM_0);
}

int main(void) {
    ternion_init(NULL);

    // Run LED_On_Off every 500 ms
    interval(LED_On_Off, 500);

    ternion_start(NULL);
    return 0;
}
```

### 1.2 Alternating Two LEDs

Controls **LED 0** and **LED 3** in opposite states so they blink in an alternating pattern. LEDs are **Active Low**: Logic Low (0) turns them ON.

```c
#include <ternion.h>

void LED_On_Off(void *p) {
    gpio_toggle_level(GPIO_LED_NUM_0);
    gpio_toggle_level(GPIO_LED_NUM_3);
}

int main(void) {
    ternion_init(NULL);

    // Start with LED 0 ON (Low), LED 3 OFF (High)
    gpio_set_level(GPIO_LED_NUM_0, GPIO_LEVEL_LOW);

    interval(LED_On_Off, 1000);  // 1 second
    ternion_start(NULL);
    return 0;
}
```

### 1.3 Key Functions (EP8)

| Function | Purpose |
|----------|---------|
| `gpio_toggle_level(GPIO_Number)` | Flips the pin state: High↔Low (LED ON↔OFF). |
| `gpio_set_level(GPIO_Number, Level)` | Sets the pin to a specific level (e.g. `GPIO_LEVEL_LOW` to turn LED ON). |
| `interval(Callback, Time_ms)` | Registers a periodic callback; runs every `Time_ms` milliseconds. |
| `ternion build flash` | Stacked command: compile then upload to the board. |

---

## 2. EP9: Switches and Events

**Video:** [EP9 – Switches and events](https://www.youtube.com/watch?v=Yul2FaMqmug&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=9)

### 2.1 Overview

A button press is an **event**. The callback is called on **press**, **release**, and **hold**. To toggle an LED only when the button is pressed (not on release), you must **filter** by checking the switch state.

### 2.2 Source Code: Switch 3 toggles LED 2

```c
#include <ternion.h>

void sw3_callback(void *param) {
    // Cast the generic pointer to switch_t * so we can read .state
    switch_t *psw = (switch_t *)param;

    // Act only on press (STATE_ON); ignore release and hold
    if (psw->state == SWITCH_STATE_ON) {
        gpio_toggle_level(GPIO_LED_NUM_2);
    }
}

int main(void) {
    ternion_init(NULL);

    // When Switch 3 has an event, call sw3_callback
    switch_set_callback(SWITCH_NUM_3, sw3_callback);

    ternion_start(NULL);
    return 0;
}
```

### 2.3 Key Concepts (EP9)

| Concept | Explanation |
|--------|--------------|
| **`switch_set_callback(Switch_Num, Callback)`** | Binds a physical switch to a function; that function runs on every switch event (press, release, hold). |
| **`void *param`** | Generic pointer passed to the callback. You must **cast** it to a concrete type before reading fields. |
| **Casting** | `(switch_t *)param` tells the compiler the pointer refers to a `switch_t`; then you can use `psw->state`. |
| **State filter** | `if (psw->state == SWITCH_STATE_ON)` runs your logic only on press, avoiding double toggles from press+release. |

**Note:** In C, `switch` is a reserved keyword. Use a different variable name for the `switch_t *` pointer (e.g. `psw`, `evt`, `sw`).

---

## 3. EP10: Analog-to-Digital Converter (ADC)

**Video:** [EP10 – ADC](https://www.youtube.com/watch?v=cqQ0Wxi7YEI&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=10)

### 3.1 Overview

The program reads **Analog Channel 1** (LDR – Light-Dependent Resistor) on a timer, then prints the value in **decimal** and **hexadecimal** to the serial monitor.

* **Gen 1:** Set the jumper to the **right** so channel 1 is connected to the LDR.
* **Gen 2:** LDR is connected by default; no jumper change needed.

### 3.2 Source Code: Read LDR and print via serial

```c
#include <ternion.h>

void read_analog(void *p) {
    uint16_t adc_val;

    adc_val = analog_read_raw(ANALOG_NUM_1);

    // %u = unsigned decimal; %04x = hex with leading zeros
    serial_printf(SERIAL_NUM_1, "Channel 1: %u (0x%04x)\r\n", adc_val, adc_val);
}

int main(void) {
    ternion_init(NULL);

    interval(read_analog, 500);  // Read every 500 ms
    ternion_start(NULL);
    return 0;
}
```

### 3.3 Key Concepts (EP10)

| Concept | Explanation |
|--------|--------------|
| **`analog_read_raw(ANALOG_NUM_n)`** | Returns the raw ADC value. **10-bit ADC** → range **0** (0 V) to **1023** (3.3 V). |
| **`ANALOG_NUM_1`** | Channel 1. On Gen 1 it is shared (jumper selects LDR vs external); on Gen 2 it connects to internal sensors. |
| **`serial_printf(SERIAL_NUM_1, format, ...)`** | Like `printf` but sends to serial port 1. Use `%u` for decimal, `%04x` for 4-digit zero-padded hex. |
| **Expected behavior** | Covering the LDR (darker) typically **increases** the value (e.g. ~300 → ~800), so you can infer light vs dark from the reading. |

---

**Last updated:** 2026-02-03
