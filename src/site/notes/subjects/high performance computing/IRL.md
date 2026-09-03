---
{"dg-publish":true,"permalink":"/subjects/high-performance-computing/irl/","dg-note-properties":{}}
---

#hpc 
- **Sequential** = Strict logical dependency (Step 2 needs Step 1's result).
- **Parallel** = Independent work that can happen at the exact same time.
- **Real-World Limit** = The parallel work _is_ parallel, but managing the processors (communication, shared memory access, synchronization) creates **overhead** that prevents the time from ever reaching true zero.
***

In pure math (Amdahl’s Law), we assume the parallel part goes to 0. In the real world, **overhead acts like a fake sequential bottleneck**. The task is still parallel, but the _logistics_ of managing thousands of processors create a physical limit.

=="logical dependency" (true sequential) and "logistical overhead" (real-world parallel limits)==

