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
