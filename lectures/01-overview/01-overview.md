# L01 – Overview

> Date: 2026-01-29

## Course Focus
This course is about learning how to use and design real computers.  
We design real bugs, find them, and remove them faster.  
We understand and improve program performance.

The important question is **how this actually works**.

Abstractions are important, but looking into the real underlying mechanisms is also important.  
It also helps to understand **what abstractions are built upon** and **what their limits are**.

---

## Critical Idea

**Ints are not Integers**  
**Floats are not Reals**

---

## Integer Issues
- Integer overflow → x² can be negative

---

## Floating-Point Issues
- Float precision problems  
- Associativity breaks

---

## Abstractions
- Abstractions hide limits  
→ Leads to bugs and surprises

---

## Characteristics of Computer Arithmetic
- Does not generate random values  
- Mathematical properties we take for granted cannot be assumed in computers

---

## Arithmetic Properties

### Integers
- Ring properties hold (commutative, associative, distributive)  
- Only when there is no overflow

### Floating Point
- Only ordering properties hold

---

## Core Warning
**Don’t assume math laws blindly**

> Date: 2026-01-29

## Computer Language Hierarchy

High-level Language → Assembly → Machine Code → Hardware

High-level language (C, etc.)  
↓ Compiler  
Assembly (.s)  
↓ Assembler  
Machine code (.o)  
↓ Linker  
Executable

---

## Why We Need to Understand Assembly

- Helps understand how programs actually behave when bugs occur  
  → The “ideal model” of high-level languages breaks under bugs  
- Enables performance tuning  
  → See why code is slow and where time is spent  
- Understand compiler optimizations (or lack of them)  
  → Explain why code was transformed  
- Precisely identify inefficiencies  
- Required for system software implementation  
  → OS, runtimes, compilers  
- The compiler’s final target is machine code  
  → Assembly is the level just above it  
- Operating systems manage process state (registers, stack, etc.)  
  → All machine/assembly-level concepts  
- Essential for malware analysis and defense  
  → Real attacks occur at machine level  
- x86 assembly is the standard choice  
  → Most real-world PCs are x86-based

---

## “System Software Is Written in Assembly” — What It Really Means

❌ Not entirely written in assembly  
⭕ Assembly is always involved

### Examples of System Software
- Operating systems (Linux, Windows)  
- Compilers  
- Runtime systems  
- Device drivers  

### Typical Composition
- Mostly written in C  
- Assembly is needed where code interacts directly with CPU

Examples of assembly-required parts:
- Bootloader  
- Context switching  
- Interrupt handling  
- System call entry/exit  
- Direct register manipulation  

These cannot be safely or fully abstracted in high-level languages.

---

## What Is x86?

x86 is a type of CPU architecture (Instruction Set Architecture, ISA).

---

## What Is an ISA?

ISA = Contract between software and hardware.

It defines:
- Available instructions (add, mov, jump…)  
- Registers and their names (%rax, %rbx…)  
- Memory addressing methods  
- Interrupt and exception handling  

Assembly language is the human-readable form of an ISA.

---

## Identity of x86

- A CPU family created by Intel  
- Standard in the PC world  

Examples:
- x86 (32-bit)  
- x86-64 / AMD64 (64-bit, modern PCs)

Thus:
- x86 CPU → runs x86 machine code  
- x86 assembly → translates into x86 machine code  
- ARM CPU → requires ARM assembly

---

## Why CS:APP Uses x86

- Most desktops and servers use x86  
- Good for explaining Linux and Windows internals  
- Industry standard  
- Connects well to debugging, reverse engineering, and security  

x86 is the ISA that best matches the real world.

---

## Common Misunderstandings

| Question | Answer |
|---------|--------|
| Is the OS written entirely in assembly? | ❌ Mostly C |
| Can you build an OS without assembly? | ⭕ Core parts require it |
| Is x86 an operating system? | ❌ CPU architecture |
| Is x86 an assembly language? | ❌ ISA (instruction set) |

---

## Memory

Memory is not unbounded.  
Relying only on high-level languages makes memory reference bugs hard to understand or debug.

---

## Performance Is More Than Big-O

Program performance is not determined by asymptotic complexity alone.

### Why Big-O Is Not Enough

1️⃣ Large constant factors  
- O(n) can be slow with big constants  
- O(n²) can be fast with good cache behavior  

2️⃣ Memory access patterns  
Example:
- copyij → 4.3ms  
- copyji → 81.8ms  

Both are O(n²), but performance differs ~20×  
→ Caused by cache and memory hierarchy (sequential vs scattered access)

3️⃣ Compiler optimizations  
- Loop unrolling  
- Vectorization  
- Register usage  

Code style affects performance even with the same algorithm.

4️⃣ Real hardware factors  
- CPU pipeline  
- Cache  
- Branch prediction  
- Memory bandwidth  

These do not appear in Big-O analysis.

---

## Core Message About Performance

To achieve good performance:
- Don’t only consider algorithms  
- Understand the system (compiler + CPU + memory)

This is why the course is called  
**Computer Systems: A Programmer’s Perspective**

**Summary:**  
Asymptotic complexity alone cannot predict real performance; constants, memory behavior, and system effects matter.

---

## Computers Do More Than Execute Programs

### I/O System

The I/O system enables programs to exchange data with the world outside CPU and memory.

---

## Programmer-Centric Approach

- Not math/theory-focused  
- Focused on system knowledge useful for real programming

---

## Knowing the System Makes You Stronger

Understanding OS, memory, and CPU behavior allows you to write code that is:
- More reliable  
- Faster  

---

## What You Gain

- More robust programs  
- Higher performance programs  

---

## OS-Level Features Covered

Hooks into the OS:
- Concurrency → multithreading, handling multiple tasks  
- Signal handlers → handling interrupts and forced events  

These topics are rarely covered in typical high-level programming courses.

---

## Unique Material

This course covers internal system behavior that is rarely taught elsewhere:
- Compilers  
- Memory  
- I/O  
- Networking realities  

---

## Not Just for Hackers

This course is not only for security experts.  
All programmers benefit from understanding systems.

---

## Bringing Out the Hidden Hacker

You learn not just to use systems, but to understand how they work internally.

---

## Final Summary

CS:APP teaches system knowledge that helps programmers write reliable, efficient, and OS-aware programs.
