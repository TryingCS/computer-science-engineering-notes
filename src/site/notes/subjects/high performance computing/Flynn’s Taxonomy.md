---
{"dg-publish":true,"permalink":"/subjects/high-performance-computing/flynn-s-taxonomy/","dg-note-properties":{}}
---

#hpc 
Classifying the Hardware ()**.

1. **Instruction Stream:** The commands the computer is executing.
2. **Data Stream:** The numbers/values the computer is working on.
---

### **The 4 Categories of Flynn’s Taxonomy**

#### **1. SISD ([[subjects/high performance computing/Single Instruction\|Single Instruction]], [[subjects/high performance computing/Single Data\|Single Data]])**
- **What it is:** One core, doing one thing to one piece of data at a time.
- **Real-world:** Your old 1990s single-core CPU. 
- **Status:** Historical baseline. We don't focus on this in HPC.

#### **2. SIMD (Single Instruction, Multiple Data)**
- **What it is:** **One** command is broadcasted, and applied to **many** pieces of data *at the exact same time*.
- **Real-world:** A GPU increasing the brightness of a 4K image. The instruction is "add 10 to the pixel value", and it does this to all 8 million pixels simultaneously. 
- **Status:** **Crucial for HPC.** This is how GPUs and CPU vector extensions (like AVX) work.

#### **3. MISD (Multiple Instruction, Single Data)**
- **What it is:** **Many** different commands are applied to the **same** piece of data.
- **Real-world:** Theoretical or highly specialized fault-tolerant systems (e.g., 3 different sensors analyzing the exact same rocket engine temperature to check for errors).
- **Status:** Rarely used in practice. Mostly academic.

#### **4. MIMD (Multiple Instruction, Multiple Data)**
- **What it is:** **Many** cores, each running its **own** independent instructions on its **own** independent data.
- **Real-world:** Your modern multi-core laptop CPU, or a massive supercomputer cluster. Core 1 might be running a web browser, while Core 2 compiles code, and Core 3 plays music.
- **Status:** **The dominant paradigm** in modern parallel computing (Multi-core CPUs, Clusters, Supercomputers).

---

### **Summary Table**
| Category | Instructions | Data     | Modern Example                   |
| :------- | :----------- | :------- | :------------------------------- |
| **SISD** | Single       | Single   | Old single-core CPU              |
| **SIMD** | Single       | Multiple | GPU, Vector processing           |
| **MISD** | Multiple     | Single   | Fault-tolerant systems (rare)    |
| **MIMD** | Multiple     | Multiple | Modern multi-core CPUs, Clusters |

---

**Check:**
Imagine a weather simulation where:
- **Processor A** is calculating wind speed.
- **Processor B** is calculating temperature.
- **Processor C** is calculating humidity.
They are all working on different parts of the map, running different math formulas, at the same time.
is this weather simulation running on a **SIMD** or **MIMD** architecture?