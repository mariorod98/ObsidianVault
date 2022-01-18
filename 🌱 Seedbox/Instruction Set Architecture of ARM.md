---
tags: state/seedling
---

# ARM Assembler [[ISA]]
RISC CPUs, in general, are *LOAD/STORE* architectures. This means that all the instructions can be grouped in two categories:
- The **operational instructions** use registers to perform an operation and store the result in another register.
- The **load/store instructions** read data from memory and store it in a register or write data from a register to memory.

## Instruction format
All the instructions have the following format:
```inst{cond}{suf} rd, {rn,} shifter```

### Instructions
Operational instructions with three operands (include ```rn```):
- ```add``` -> "+". ```add r1, r2, #33``` -> r1 = r2 + 33.
- ```sub``` -> "-". ```sub r1, r2, #33``` -> r1 = r2 - 33.
- ```rsb``` -> "-" (in inverse order). ```sub r1, r2, #33``` -> r1 = 33 - r2.
- ```eor``` -> "^" (xor). ```eor r1, r2, r3``` -> r1 = r2 ^ r3.
- ```orr``` -> "|" (or). ```orr r1, r2, r3``` -> r1 = r2 | r3.
- ```and``` -> "&" (and). ```and r1, r2, r3``` -> r1 = r2 & r3.
- ```bic``` -> "& ~" (and not). ```bic r1, r2, r3``` -> r1 = r2 & (~r3).
- ```adc``` -> "+" with carry.
- ```sbc``` -> "-" with carry.

Instructions with two operands (do not include ```rn```):
- ```mov``` -> "=". ```mov r1, r2``` -> r1 = r2.
- ```mvn``` -> "~" (not). ```mvn r1, r2``` -> r1 = ~r2.

Comparisons:
To compare two values, we use ```cmp``` and ```cmn```. These operations act as an ```add``` and ```sub```, respectively. The difference is that the latter store the result in a register and updates the corresponding flags, while the former discards the result and only updates the corresponding flags. The flags are stored in the [[Registers in ARM]].
- ```cmp r1, #33```-> r1 + 33 and update flags.
- ```cmn r1, #33``` -> r1 - 33 and update flags.  

Comparisons can have a conditional suffix but it is not recommended.



### Conditionals
All instructions can have a conditional suffix attached that determines whether the instruction will be executed or not. This conditions relies on the results of the previous operation.

- ```eq``` -> equals.
- ```ne``` -> not equals.
- ```gt``` -> greater than (signed).
- ```lt``` -> lower than (signed).
- ```ge``` -> greater or equal than (signed).
- ```le``` -> lower or equal than (signed).
- ```hi``` -> greater than (unsigned).
- ```lo``` -> lower than (unsigned).
- ```he``` -> greater or equal than (unsigned).
- ```ls``` -> lower or equal than (unsigned).
- ```mi``` -> is negative.
- ```pl``` -> is positive (including 0).
- ```cs``` -> carry set (a sum/sub exceeded the available bits).
- ```cc``` -> carry clear (a sum/sub didn't exceed the available bits).
- ```vs``` -> overflow (the sign of the sum/sub is incorrect doe to carrying).
- ```vc``` -> there was no overflow.

Examples:
```sub r1, r2, #3``` -> x = y - 3.
```cmp r1, #0```-> compare r1 to 0 and update flags.
```movle r1, #0``` -> if r1 < 0 then r1 = 0.

### Suffix
The second suffix of the operation can be ```s``` to compare the result with 0.

```subs r4, r5, r6``` -> r4 = r5 - r6;
```movlt r5, r4``` -> if(r4 < 0){r5 = r4};

### Shifter
The shifter is a flexible operand that can adopt the following values:
- A register. ```add r0, r1, r2```.
- A constant in:
    - decimal. ```add r0, r1, #10```.
    - hexadecimal. ```add r0, r1, #0xF```.
- A register with [[bit shifting]].
    - Shift to the right (unsigned). ```mov r0, r1, lsr #3``` -> r0 = r1  >> 3.
    - Shift to the right (signed). ```mov r0, r1, asr #3``` -> r0 = r1  >> 3.
    - Shift to the left. ```mov r0, r1, lsl #3``` -> r0 = r1 << 3.

---
Planted: 2022-01-18
Last tended: 2022-01-18
