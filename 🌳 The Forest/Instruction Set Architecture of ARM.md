tags: #state/bud #on/assembler


# ARM Assembler [[ISA]]
==RISC CPU's==, in general, ==are *LOAD/STORE* architectures==. This means that all the instructions can be grouped in three categories (with some exceptions depending on the CPU):
- The **operational instructions** use registers to perform an operation and store the result in another register.
- The **load/store instructions** read data from memory and store it in a register or write data from a register to memory.
- The **flow control instructions** are instructions used to jump to specific parts of the code.

### Instruction format
All the instructions have the following format:
`inst{cond}{suf} rd, {rn,} {shifter}`

### Operational instructions with integers
**Operational instructions with three operands (include `rn`)**

| Instruction | Example | Operation |
|:---:|---|---|
|`add`|`add r1, r2, #33`|r1 = r2 + 33|
|`sub`|`sub r1, r2, #33`|r1 = r2 - 33|
|`rsb`|`rsb r1, r2, #33`|r1 = 33 - r2|
|`eor`|`eor r1, r2, r3`|r1 = r2 ^ r3|
|`orr`|`orr r1, r2, r3`|r1 = r2 | r3|
|`and`|`and r1, r2, r3`|r1 = r2 & r3|
|`bic`|`bic r1, r2, r3`|r1 = r2 & (~r3)|
|`adc`|`add r1, r2, #33`|r1 = r2 + 33 (with carry)|
|`sbc`|`sub r1, r2, #33`|r1 = r2 - 33 (with carry)|

**Operational instructions with two operands (do not include `rn`)**

| Instruction | Example | Operation |
|:---:|---|---|
|`mov`|`mov r1, r2`|r1 = r2|
|`mvn`|`mvn r1, r2`|r1 = ~r2|

**Operational instructions that do not admit constants in the shifter operand, only registers**

| Instruction | Example | Operation |
|:---:|---|---|
|`mul`|`mul r0, r1, r2`|r0 = r1 \* r2|
|`mla`|`mla r0, r1, r2, r3`|r0 = r1 \* r2 + r3|
|`clz`|`clz r0, r1`|Counts the number of leading zeroes<br/>in r1 and store that number in r0|

Some considerations to take into account:
- ==clz only admits conditional suffixes==.
- In the first ARM CPUs, mul couldnt repeat the same register in rd and rn.
    - `mul r0, r0, r1` is illegal.
    - `mul r0, r1, r0` is legal.
### LOAD/STORE instructions
The general LOAD/STORE instruction format is:
`inst{cond} rd, [address]`

| Instruction | Operation | Type |
|:---:|---|---|
|`ldrb`|Reads a byte (8 bits)|unsigned char|
|`ldrsb`|Reads a byte (8 bits) and carry the sign|signed char|
|`ldrh`|Reads a halfword (16 bits)|unsigned short|
|`ldrsh`|Reads a halfword (16 bits) and carry the sign|signed short|
|`ldr`|Reads a word (32 bits)|unsigned/signed int and pointer|
|`strb`|Writes a byte (8 bits)|unsigned/signed char|
|`strh`|Writes a halfword (16 bits)|unsigned/signed short|
|`str`|Writes a word (32 bits)|unsigned/signed int and pointer|

There are several ways to specify an address (addressing modes):

| Instruction | Operation |
|:---:|---|---|
|`[reg.]`|\*ptr|
|`[reg.], #num`|\*ptr += num OR \*ptr++|
|`[reg., #num. offset]`|\*ptr  + offset|
|`[reg., reg.]`|\*ptr + x|
|`[reg., reg., lsl #num]`|\*ptr + (x << num)|
|`[reg., reg., lsr #num]`|\*ptr + (x >> num) (unsigned)|
|`[reg., reg., asr #num]`|\*ptr + (x >> num) (signed)|

Examples:
```
    ldr r4,[r5]               @ r4 = *r5
    ldr r2,[r1, r3, lsl #2]   @ r2 = r1[r3 << 2] r3 is multiplied by 4 because it is an int pointer (4 bytes)
    ldrb r2,[r1,r3]           @ r2 = r1[r3], there is no need to multiply because it is a byte.
    ldr r0,[r3],#4            @ r0 = *r3++, because it is an int, you have to add 4 bytes
    str r0,[r1]               @ *r1 = r0
    strb r3,[r6,#5]           @ r6[5] = r3, r6 is a char pointer
    str r3,[r6,#5]            @ r6[5] = r3, r6 is a int pointer
```


**Common pitfall**
All the LOAD/STORE instructions support conditional suffixes. But, ==LOAD/STORE instructions that do not operate a full word have the conditional in between the instruction==.
```
    ldreq  r4,[r5] @ r4 = *r5
    ldreqh r4,[r5] @ r4 = *r5
    ldreqb r4,[r5] @ r4 = *r5

    strgt  r4,[r5] @ r4 = *r5
    strgth r4,[r5] @ r4 = *r5
    strgtb r4,[r5] @ r4 = *r5
```
### Flow control instructions
**Comparisons**
In the ARM architecture, there is a special register, the [[Registers in ARM Assembler|Status Register]], that stores the logical results of operations. These results are written when executing comparisons and are read when a conditional suffix is present.

To compare two values, we use `cmp` and `cmn`. These operations act as an `subs` and `adds`, respectively. The difference is that the latter store the result in a register and updates the corresponding flags, while the former discards the result and only updates the corresponding flags.
- `cmp r1, #33`-> r1 - 33 and update flags.
- `cmn r1, #33` -> r1 + 33 and update flags.  

==Comparisons can have a conditional suffix but it is not recommended.==

**Inconditional jump**

The instruction `b` is used to jump to any point in the program. It must be followed by a tag, this tag must be declared somewhere in the program. For example, in the next snippet of code, the instruction `b` sets the program counter to the instruction`add`. Therefore, the instruction `mov` will never be executed:
```
    b Jump
    mov r0, r1
    ...
Jump:
    add r0, r1, r2
```
**Jump with return**
The instruction `bl` is used to jump to a subroutine. When executing this instruction, the following instruction is stored in the [[Registers in ARM Assembler|Link Register]]. It is the [[C_C++|C]] equivalent to calling a function.
```
    bl Squared
    add r0, r0, #1
    ...
Squared:
    mul r0, r1, r1
    bx lr
```
%% TODO %%
%%WHAT IS bx USED FOR? %%
%% WHAT DOES exchange instruction set MEAN?%%

**Jump to a pointer**
It is possible to jump to a direction stored in a register. The following instructions execute the same jump to the direction stored in r1:
```
    mov pc, r1
    b r1
    bx r1
```
### Conditionals
All instructions can have a conditional suffix attached that determines whether the instruction will be executed or not. This conditions relies on the results of the previous operation.

| Instruction | Definition |
|:---:|---|
|`eq`|equals|
|`ne`|not equals|
|`gt`|greater than (signed)|
|`lt`|lower than (signed)|
|`ge`|greater or equal than (signed)|
|`le`|lower or equal than (signed)|
|`hi`|greater than (unsigned)|
|`lo`|lower than (unsigned)|
|`he`|greater or equal than (unsigned)|
|`ls`|lower or equal than (unsigned)|
|`mi`|is negative|
|`pl`|is positive (including 0)|
|`cs`|carry set (a sum/sub exceeded the available bits)|
|`cc`|carry clear (a sum/sub didn't exceed the available bits)|
|`vs`|overflow (the sign of the sum/sub is incorrect doe to carrying)|
|`vc`|there was no overflow|

Examples:
**Clamp a negative number to 0**
`sub r1, r2, #3` -> x = y - 3.
`cmp r1, #0`-> compare r1 to 0.
`movlt r1, #0` -> if r1 < 0 then r1 = 0.

**Min between two numbers**
`cmp r1,r0`  -> compares r1 and r0 
`movlt r0,r1` -> if r1 < r0, then r0 = r1

### Suffix
In arithmetic operations, the second suffix of the operation can be `s` to compare the result with 0.

`subs r4, r5, r6` -> r4 = r5 - r6;
`movlt r5, r4` -> if(r4 < 0){r5 = r4};

### Shifter
The shifter is a flexible operand that can adopt the following values:
- A register. `add r0, r1, r2`.
- A constant in:
    - decimal. `add r0, r1, #10`.
    - hexadecimal. `add r0, r1, #0xF`.
- A register with [[Bit Shifting]].
    - Shift to the right (unsigned). `mov r0, r1, lsr #3` -> r0 = r1  >> 3.
    - Shift to the right (signed). `mov r0, r1, asr #3` -> r0 = r1  >> 3.
    - Shift to the left. `mov r0, r1, lsl #3` -> r0 = r1 << 3.


### Interesting functions
**Abs function*
```
if(a < 0)
    a = -a

    cmp   r0,#0            @ if a < 0
    sublt r0,r0,r0,lsl #1  @ a = a - 2 * a

@ Other approximation
    cmp   r0,#0     @ if a < 0
    rsblt r0,r0,#0  @ a = 0 - a

```
---
Planted: 2022-01-18
Last tended: 2022-02-01