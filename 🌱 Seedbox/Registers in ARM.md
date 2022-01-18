---
tags: state/seedling
---

# Registers in ARM
- **General-purpose registers R0-R12**.
- **Stack Pointer (SP)**.
- **Link Register (LR)**
- The **Program Counter (PC)**
- The **Status Register (SR)** holds copies of the conditional flags that the processor uses to determine whether to execute conditional instructions. The conditional flags are:
    - The Negative flag, **N**, copies the sign bit (bit 31) of the last operation. 1 = negative, 0 = positive.
    - The Overflow flag, **V**, is 1 when the last sum/sub cause overflow of a signed number.
    - The Zero flag, **Z**, is 1 when the result of the last operation is 0.
    - The Carry flag, **C**, is 1 when the last operation results in carry.

---
Planted: 2022-01-18
Last tended: 2022-01-18