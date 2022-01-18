---
tags: state/seedling
---

# Registers in ARM
The ARM Assembler has 16 registers divided in:

- **General-purpose registers R0-R12**. In C, the processor will try to map local variables to registers if they are available. Otherwise, the variables will be stored in the stack.
- R13: **Stack Pointer (SP)**.
- R14: **Link Register (LR)**.
- R15: The **Program Counter (PC)** It stores the direction of the instruction n + 2, where n is the current instruction being executed.

The ARM Assembler also includes a special register, the **Status Register (SR)**, that holds copies of the conditional flags that the processor uses to determine whether to execute conditional instructions. The conditional flags are:
    - The Negative flag, **N**, copies the sign bit (bit 31) of the last operation. 1 = negative, 0 = positive.
    - The Overflow flag, **V**, is 1 when the last sum/sub cause overflow of a signed number.
    - The Zero flag, **Z**, is 1 when the result of the last operation is 0.
    - The Carry flag, **C**, is 1 when the last operation results in carry.

---
Planted: 2022-01-18
Last tended: 2022-01-18