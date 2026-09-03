---
{"dg-publish":true,"permalink":"/subjects/high-performance-computing/single-data/","dg-note-properties":{}}
---

#hpc 
## **What is a "Piece of Data"?**

A **piece of data** is the **value(s)** that an instruction operates on.

### **At the Smallest Level:**
- **Example:** A single **number** (integer, float)
- **Size:** 
  - 32-bit float: **4 bytes**
  - 64-bit double: **8 bytes**
  - 8-bit integer: **1 byte**

### **At Larger Levels:**
- **Example:** 
  - A **vector** of 1,000 numbers
  - A **matrix** of 10,000 × 10,000 elements
  - An entire **image** (millions of pixels)
  - A **database record**

---

## **Concrete Example: Vector Addition**

Let's say you're adding two arrays: `C = A + B`

### **Scenario 1: SISD (Old Single-Core CPU)**
- **Instruction Stream:** ONE stream (the CPU fetches one instruction at a time)
- **Data Stream:** ONE piece at a time
- **Execution:**
  ```
  Instruction 1: ADD A[0] + B[0] → C[0]
  Instruction 2: ADD A[1] + B[1] → C[1]
  Instruction 3: ADD A[2] + B[2] → C[2]
  ... (one at a time, sequentially)
  ```

### **Scenario 2: SIMD (GPU or Vector Unit)**
- **Instruction Stream:** ONE instruction broadcasted
- **Data Stream:** MULTIPLE data elements simultaneously
- **Execution:**
  ```
  Instruction: ADD (broadcasted once)
  Data: A[0], A[1], A[2], A[3] + B[0], B[1], B[2], B[3] → C[0], C[1], C[2], C[3]
  ```
  **One instruction** operates on **4 (or 8, or 16, or thousands) of data elements** at the exact same time.

### **Scenario 3: MIMD (Modern Multi-Core CPU)**
- **Instruction Stream:** MULTIPLE independent instructions
- **Data Stream:** MULTIPLE independent data elements
- **Execution:**
  ```
  Core 1: ADD A[0] + B[0] → C[0]  (running its own program)
  Core 2: MUL X[5] * Y[5] → Z[5]  (running a DIFFERENT program!)
  Core 3: SQRT(D[10]) → E[10]     (running yet ANOTHER program!)
  ```
  Each core runs **different instructions** on **different data**.

---

## **How Small or Big Can They Be?**

| Component       | Minimum Size           | Typical Size              | Maximum Size                     |
| --------------- | ---------------------- | ------------------------- | -------------------------------- |
| **Instruction** | 1 machine op (4 bytes) | 1 high-level statement    | Entire program (millions of ops) |
| **Data**        | 1 bit                  | 4–8 bytes (single number) | Terabytes (entire dataset)       |

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

## **Quick Check:**

In the context of Flynn's Taxonomy, when we say:
- **"Single Instruction"** → We mean the *same operation* is being performed (e.g., "ADD" everywhere)
- **"Multiple Data"** → We mean that operation is applied to *many different values* simultaneously (e.g., adding millions of numbers)