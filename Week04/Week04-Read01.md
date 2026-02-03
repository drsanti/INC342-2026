# Week 4 Reading Material: Periodic Operations, User Input, and ADC

**Companion:** [Week04-Read02](Week04-Read02.md) (code examples) · **Self-test:** [Week04-Test01](Week04-Test01.md)

---

**Video resources (EmbSysDev playlist):**

| Topic | Video | Link |
|-------|--------|------|
| **EP8** – Periodic operations & LED control | Index 8 | [YouTube](https://www.youtube.com/watch?v=vuMPcCpqx5k&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=8) |
| **EP9** – Handling user input: switches and events | Index 9 | [YouTube](https://www.youtube.com/watch?v=Yul2FaMqmug&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=9) |
| **EP10** – Analog-to-digital converters (ADC) | Index 10 | [YouTube](https://www.youtube.com/watch?v=cqQ0Wxi7YEI&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=10) |

---

## 1. Periodic Operations and LED Control

**Video:** [EP8 – Blinking LED](https://www.youtube.com/watch?v=vuMPcCpqx5k&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=8)

This module introduces the “Hello World” of embedded systems: the **blinking LED**. You will use **periodic operations**—tasks that repeat at a fixed time interval (like clapping to a rhythm)—and the Ternion APIs that support them.

### 1.1 Essential Updates

Before starting a new module, always check **Ternion DevTools** for updates.

* **Check the date:** Open the project’s GitHub page and check the “Last Update” date. If the software was updated after you installed it, update your installation.
* **Installation tip:** If the installer does nothing when run, hold **Shift**, right‑click the installer, choose **“Copy as path”**, then run that path in Command Prompt (Run as administrator).

### 1.2 Project Creation

Create a new project with an explicit directory name instead of using the current folder:

* **Command:** `ternion create ep08_blinking_led`
* **Result:** A new folder `ep08_blinking_led` is created with the required project files.

### 1.3 Board Selection (Important)

The toolchain defaults to **Gen 1**. If you use a **Gen 2** board, you must switch the target:

* **Command:** `ternion select gen2`
* **Reason:** Gen 1 and Gen 2 differ in hardware; the library must know which board to target.

### 1.4 Blinking Logic

Blinking is implemented with an **interval** (similar to `setInterval` in JavaScript):

1. **Callback:** Implement a function (e.g. `led_toggle`) that runs every time the timer fires.
2. **Toggle:** Inside that function, call `gpio_toggle_level(GPIO_LED_NUM_0)` to flip the LED state (ON↔OFF).
3. **Build and flash:** You can run build and flash in one step: `ternion build flash`. This builds and then flashes the board after a successful build.

---

## 2. Handling User Input: Switches and Events

**Video:** [EP9 – Switches and events](https://www.youtube.com/watch?v=Yul2FaMqmug&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=9)

Here we work with **events**. A button press is an event: the user acts on the hardware, and the microcontroller receives and handles it.

### 2.1 The “Press” Problem

If you toggle an LED directly inside the button callback, the LED may seem to behave oddly. **Pressing** and **releasing** the button are both events. If you do not filter by event type, the LED will toggle on press *and* on release.

### 2.2 Event Filtering

Use the data passed into the callback to run your logic only when the button is actually pressed:

1. **The callback parameter:** The callback receives `void *param`—a generic pointer (like a sealed box) that you must interpret.
2. **Casting:** Cast it to the correct type, e.g. `switch_t *evt = (switch_t *)param`.
3. **Checking state:** Use the `state` field of that pointer. For example:
   * **Logic:** `if (evt->state == SWITCH_STATE_ON)`
   * This runs only when the button is pressed (ON), and ignores release or other states.

**Note:** In C, `switch` is a reserved keyword. Use a different variable name (e.g. `evt`, `sw`, `switch_evt`) for the `switch_t *` pointer.

---

## 3. Sensing the World: Analog-to-Digital Converters (ADC)

**Video:** [EP10 – ADC](https://www.youtube.com/watch?v=cqQ0Wxi7YEI&list=PLBPFpqyTjzeXu0P0vRzooo-VWmZtSZkAj&index=10)

Digital systems use 0s and 1s; the physical world is analog. An **ADC (Analog-to-Digital Converter)** bridges the two by turning a voltage (e.g. 0 V–3.3 V) into a digital value (e.g. 0–1023).

### 3.1 Hardware: LDR (Light-Dependent Resistor)

We use an **LDR**, a sensor whose resistance changes with light level.

* **Gen 1:** Move the **jumper** on the board to the **right** so that analog channel 1 is connected to the LDR.
* **Gen 2:** No jumper change is needed; the board has two built-in LDRs connected to the MCU.

### 3.2 Reading and Viewing ADC Data

* **Read the sensor:** `val = analog_read_raw(ANALOG_NUM_1);`
* **Send to PC:** Use `serial_printf` to print the value to the serial monitor.
* **Observe:** When you cover the sensor, the printed values change (e.g. from around 300 to 800), showing that the system is measuring light intensity.

---

**Last updated:** 2026-02-03
