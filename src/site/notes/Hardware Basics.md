---
{"dg-publish":true,"permalink":"/hardware-basics/","dg-note-properties":{}}
---

#hpc 
### 💾 Hardware Basics: Strict Summary

**Transistors & Logic**
*   **Transistor:** A microscopic electrically controlled switch. Has two states: On (1) or Off (0).
*   **Logic Gates:** Transistors wired together to perform basic boolean logic (AND, OR, NOT).
*   **CPU:** Billions of logic gates organized into:
    *   **ALU (Arithmetic Logic Unit):** Performs math and logic.
    *   **Control Unit:** Directs data flow and instruction execution.
    *   **Registers:** Ultra-fast, tiny memory slots inside the CPU.

**Clock & Time**
*   **Clock Speed:** The frequency of the CPU's internal metronome (Hz). The tempo at which operations occur.
*   **Clock Domain:** The localized "world" of a specific component. Transistors have no concept of time outside their domain; they only react to voltage when the clock ticks.
*   **Propagation Delay:** The physical time it takes for electricity to travel through wires and flip transistors. This sets the hard physical limit on maximum clock speed.
*   **Dynamic Frequency Scaling:** Clock speed is not permanently hardcoded. The CPU adjusts it on the fly based on workload and temperature (e.g., dropping to 800 MHz to save battery, boosting to 4.5 GHz for heavy tasks).

**Performance & Architecture**
*   **Performance = Clock Speed × IPC (Instructions Per Cycle).**
*   **IPC:** The amount of work done per clock tick. Increased through architecture, not just faster ticking.
*   **Pipelining:** Overlapping instruction execution (like an assembly line) so different stages of multiple instructions run simultaneously.
*   **Superscalar Execution:** Having multiple ALUs so several independent instructions can execute in the exact same clock tick.
*   **Out-of-Order Execution:** Doing independent work while waiting for slow memory operations to finish.
*   **Branch Prediction:** The CPU guesses the outcome of an `if` statement to keep the pipeline full.
    *   *Correct guess:* Zero time lost.
    *   *Misprediction:* The pipeline is flushed. All speculative work is thrown away, wasting clock cycles.
*   **Cache (L1, L2, L3):** Small, very fast memory located close to the CPU to avoid the massive latency of going to RAM.

**Hardware Reality & Limits**
*   **Dennard Scaling (Ended mid-2000s):** Shrinking transistors no longer kept power density constant. Increasing clock speed caused exponential heat and power consumption.
*   **The Wall:** Engineers could not crank clock speed higher without melting chips.
*   **The Solution:** Stop increasing single-core clock speed. Instead, add multiple processing units (Cores) to the same chip -> **Parallel Computing**.
*   **Transistor Failure:** A dead transistor usually breaks logic, crashing the machine, rather than just slowing it down. 
*   **Binning:** If a transistor in a multi-core chip is defective, manufacturers disable that core and sell the chip as a lower-tier model (e.g., an 8-core chip with one dead core becomes a 7-core chip).

---

