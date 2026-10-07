---
{"dg-publish":true,"permalink":"/fault-tolerance/","created":"2026-10-04T03:41:45.406+01:00","updated":"2026-10-04T03:42:47.614+01:00","dg-note-properties":{}}
---

#hpc 
###  Question: What if some transistors die?

The answer is: **It usually ruins the whole machine, not just changes the path.**

Unlike a city traffic jam where you can just take a detour, a CPU is a highly precise mathematical machine. If a transistor dies, it usually breaks the *logic*, not the *speed*.

*   **Manufacturing Defects (The "Binning" Process):** When a CPU is manufactured, it is tested. If a transistor in Core #7 is dead, the manufacturer doesn't throw away the whole chip. They **disable Core #7** and sell the chip as a cheaper model (e.g., an 8-core chip with one dead core becomes a 7-core chip). This is called "binning." It's why you can buy a 6-core and an 8-core version of the same CPU—they are often physically identical, but the 6-core just had two defective cores that were turned off.
*   **Runtime Failures (Electromigration):** Transistors can die over time due to heat and voltage stress. If a critical transistor in the Control Unit dies, the CPU will instantly crash (Blue Screen of Death / Kernel Panic). It doesn't just run slower; it produces garbage math and the computer halts.
*   **Error Correction:** In high-end servers (like those running HPC clusters), they sometimes use **ECC memory** (Error Correcting Code) to detect and fix bit flips caused by dying transistors. But if the actual CPU logic dies, the machine goes down.
*   **Redundancy:** Some spacecraft and fault-tolerant systems have *extra* cores that do the same work simultaneously and "vote" on the answer. If one core dies, the others outvote it. But your standard laptop CPU doesn't do this; it just crashes.

**So, to answer directly:** A dead transistor doesn't change the "longest path." It breaks the logic. It's like removing a brick from a Jenga tower—the tower doesn't just get shorter, it collapses.
