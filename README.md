# STM32 FreeRTOS Demo Project  

This project is **not a commercial product** — it’s a learning and demonstration project I built to strengthen my embedded systems skills and to show my capability with **FreeRTOS on STM32 microcontrollers**.  

The goal is to prove (to myself and to potential employers) that I can **configure, structure, and program RTOS-based applications** on STM32 platforms — moving beyond academic research and into practical, industry-ready development.  

---

## 🔹 Features  

- **RTOS Integration (FreeRTOS):**
  - Task creation and scheduling  
  - Queues, semaphores, and mutexes  
  - Event groups for inter-task signaling  
  - Software timers for periodic events  

- **UART Interrupt-based Communication:**
  - Receives commands (`START`, `STOP`, `GET`) from the serial terminal  
  - Command parsing is interrupt-driven, not polling-based  

- **Sensor Simulation with ADC:**
  - Periodically reads a value from ADC (or simulated input)  
  - Sends the reading to a queue for further processing  

- **Data Logging Task:**
  - Stores ADC readings in a circular buffer  
  - Logging is enabled/disabled via UART commands  
  - Supports `GET` command to transmit logged values back over UART  

- **LED Status Indicator (on-board LED):**
  - Slow blink → System idle  
  - Fast blink → Logging active  
  - Rapid blink → Error state (for demonstration)  

---

## 🔹 How It Works  

- **Sensor Task**  
  Periodically reads ADC values and sends them to a queue.  

- **Logger Task**  
  Receives values from the queue and stores them in a circular buffer (protected by a mutex).  

- **Communication Task**  
  Handles UART input from the user:
  - `START` → Enables logging  
  - `STOP` → Disables logging  
  - `GET` → Dumps logged ADC values over UART  

- **LED Timer Callback**  
  Blinks the on-board LED with a period depending on the system state.  

This structure demonstrates **practical RTOS concepts** such as task synchronization, inter-task communication, and interrupt handling.  

---

## 🔹 Hardware & Tools  

- **Board:** STM32F746ZG Discovery Board  
- **IDE:** STM32CubeIDE  
- **RTOS:** FreeRTOS (configured via CubeMX)  
- **Communication:** UART3 @ 115200 baud (via USB to PC)  
- **Terminal:** HTerm, TeraTerm, PuTTY, or similar  

---
