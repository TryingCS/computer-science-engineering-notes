---
{"dg-publish":true,"permalink":"/adding-vs-shrinking/","dg-note-properties":{}}
---

#hpc 
if more transistors = more complex circuits = longer wires, how  did clock speed increase?

The answer lies in a crucial distinction: **Adding transistors vs. Shrinking transistors.** 

In the pre-parallelism era (roughly the 1970s to the mid-2000s), engineers were doing **both** at the same time. Here is exactly how it worked.

### 1. The Shrinking (The Real Speedup)
If you just added more transistors to a CPU without shrinking them, the physical chip would become the size of a pizza box. The wires would get longer, electricity would take forever to travel, and clock speed would plummet. 

But that's not what happened. Engineers were following **Moore's Law**: they were constantly **shrinking the transistors themselves**. 

When you shrink a transistor:
*   It requires less voltage to flip on and off.
*   It has less electrical capacitance (it stores less energy).
*   **Crucially:** The wires connecting them get shorter because the transistors are packed closer together.

By shrinking everything, the "road" that electricity had to travel actually got **shorter**, not longer. Because the road got shorter, electricity could reach the end faster. This meant the clock tick could happen faster. **This is what drove clock speeds from 10 MHz in the 1980s to 4 GHz in the 2000s.**

### 2. The Adding (The "Talent")
So if shrinking made things faster, why add more transistors? 
Because the shrinking process freed up physical space on the chip. Engineers could now fit *more* transistors in the same physical area. 

They used this extra "transistor budget" to build the smart architecture features :
*   **Pipelining:**  used transistors to build assembly-line stages. Instead of one long road where electricity has to travel all the way across the chip to finish an instruction, they built checkpoints. The instruction travels a short distance, gets saved in a register (a checkpoint), and the next tick moves it to the next stage. **Pipelining actually *shortens* the longest path electricity has to travel in a single tick, allowing the clock to tick even faster.**
*   **Branch Prediction:** They used transistors to build tiny memories that remember past `if` statements. 
*   **Multiple ALUs:** They added more calculators.🧮

### 3. The Pre-Parallelism Summary
So, in the single-core era:
*   **Transistors shrank** \(\rightarrow\) Wires got shorter \(\rightarrow\) Electricity traveled faster \(\rightarrow\) **Clock speed increased.**
*   **Transistors were added** (using the freed-up space) \(\rightarrow\) Built smarter logic (pipelining, prediction) \(\rightarrow\) **IPC increased.**

Performance = Clock Speed × IPC. Both were going up simultaneously. 

### 🛑 The Wall (Why it stopped)
By the mid-2000s, transistors got so small that they couldn't shrink them anymore without them leaking electricity and generating insane heat (The End of Dennard Scaling). 

Engineers could no longer shorten the wires or increase the clock speed. They could still *add* more transistors, but adding more to a single core just made it too hot and too complex. 

So, they used the extra transistors to build **a second core**. And a third. And a fourth. 

**The road inside a single core stopped getting shorter. So they built multiple roads.**

---

Does this clear up the paradox? The speed didn't come from the road getting *longer*; it came from the transistors shrinking, which made the road *shorter* and allowed the clock to tick faster. The extra transistors were used for smarter logic, not just longer wires. 

