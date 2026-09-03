---
{"dg-publish":true,"permalink":"/subjects/high-performance-computing/single-instruction/","dg-note-properties":{}}
---

#hpc 
## **What is an "Instruction"?**

An **instruction** is a **single command** that tells the processor what operation to perform.

### **At the Hardware Level (Smallest):**
- **Example:** `ADD` (addition), `MUL` (multiplication), `LOAD` (read from memory)
- **Size:** Typically **4–8 bytes** in machine code
- **Real Assembly Example:**
  ```assembly
  ADD R1, R2, R3    ; Instruction: Add contents of R2 and R3, store in R1
  ```
  This is **one instruction**.

### **At the High-Level (Larger):**
- **Example:** In C code: `C[i] = A[i] + B[i];`
- **What it compiles to:** This *single line* of C might become **3–5 machine instructions**:
  1. `LOAD` A[i] into register
  2. `LOAD` B[i] into register  
  3. `ADD` the two registers
  4. `STORE` result into C[i]

**Key Point:** In Flynn's Taxonomy, we usually think of instructions at the **machine code level** (what the CPU actually executes), not the high-level source code.

---


## **How Small or Big Can They Be?**

| Component | Minimum Size | Typical Size | Maximum Size |
|-----------|-------------|--------------|--------------|
| **Instruction** | 1 machine op (4 bytes) | 1 high-level statement | Entire program (millions of ops) |
| **Data** | 1 bit | 4–8 bytes (single number) | Terabytes (entire dataset) |

### **Real-World Scale Examples:**

**Small Scale:**
- Instruction: `ADD R1, R2` (one CPU cycle)
- Data: Two 32-bit integers

**Medium Scale:**
- Instruction: "Apply Gaussian blur filter" (one GPU kernel launch)
- Data: A 1920×1080 image (2 million pixels)

**Large Scale:**
- Instruction: "Train this neural network" (one distributed job)
- Data: 100 TB dataset across 1,000 nodes

---


In the context of Flynn's Taxonomy, when we say:
- **"Single Instruction"** → We mean the *same operation* is being performed (e.g., "ADD" everywhere)
- **"Multiple Data"** → We mean that operation is applied to *many different values* simultaneously (e.g., adding millions of numbers)

"the command" ==> (instruction) 
"the values being operated on ==>(data) 
