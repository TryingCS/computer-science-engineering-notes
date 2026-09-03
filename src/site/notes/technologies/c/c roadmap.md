---
{"dg-publish":true,"permalink":"/technologies/c/c-roadmap/","dg-note-properties":{}}
---

#c 
for **low-level performance, memory control, and parallel computing**.

---

## Must know before Semester 7

| Topic            | should know                                   |
| ---------------- | --------------------------------------------- |
| Basic syntax     | Variables, loops, `if`, functions             |
| Types            | `int`, `float`, `double`, `char`, arrays      |
| Pointers         | `*`, `&`, pointer arithmetic                  |
| Memory           | Stack vs heap, `malloc`, `free`, memory leaks |
| Arrays / strings | C-style arrays, `char*`, string functions     |
| Structs          | `struct`, `typedef`                           |
| File I/O         | `fopen`, `fclose`, `fread`, `fwrite`          |
| Compilation      | `gcc file.c -o program`                       |
| Makefiles        | Basic `make` usage                            |
| Debugging basics | `printf`, `gdb`, segmentation faults          |

---

##  before HPC

| Topic | Why |
|---|---|
| Pointers and memory layout | Needed for MPI, OpenMP, PThreads, CUDA |
| Multithreading basics | Needed for PThreads and OpenMP |
| Compilation flags | `-O2`, `-O3`, `-Wall`, `-pthread` |
| Valgrind | Detect memory leaks and invalid accesses |
| Linux CLI | Compile, run, measure time |
| Basic bash | Run scripts and jobs |

---

## through courses

| Course                             | concepts learned                                                                                           |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| High-Performance Computing         | MPI, OpenMP, PThreads, CUDA/OpenCL, parallel loops, message passing, GPU kernels, performance optimization |
| Data Security                      | Memory vulnerabilities, buffer overflows, exploit basics, secure coding                                    |
| Image Processing / Computer Vision | Mostly C++ with OpenCV, but may touch performance-focused image code                                       |
| Bio-inspired Methods               | Possibly C/C++ for fast simulation of genetic algorithms/swarms                                            |
| Big Data / Distributed             | Less C, more Java/Scala/Python, but C may appear in low-level tools                                        |

---

###  before 7

  understand this:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n = 5;
    int *arr = malloc(n * sizeof(int));

    for (int i = 0; i < n; i++) {
        arr[i] = i * 2;
    }

    for (int i = 0; i < n; i++) {
        printf("%d\n", arr[i]);
    }

    free(arr);
    return 0;
}
```

Compile:

```bash
gcc test.c -o test
./test
```

---

Before Semester 7: learn **pointers, memory management,structs,arrays, gcc, Makefiles**.

During Semester 7 HPC: you will likely learn **OpenMP, MPI, PThreads, CUDA/OpenCL, and performance profiling**.

