
---
tags: state/bud on/math on/computerScience
---

# Bit Shifting
Bit shifting is an operation that shifts the value of a binary number to the right or the left. There are four different types of shifting.

### Left Shift
Left shifting, usually written as `<<`,  is the operation that shifts all the numbers to the left. It introduces 0s in the emptied positions.
```
00000000 00000000 00000000 00001111 << 4 = // 15
00000000 00000000 00000000 11110000        // 240
```

A single left shift multiplies a binary number by 2:
```
00000000 00000000 00000000 00001100 << 1 = // 12
00000000 00000000 00000000 00011000        // 24
```

### Right shift
Right shifting, usually written as `>>`, is the operation that shifts all the numbers to the left. If the binary number is unsigned, it introduces 0s. If the binary number is signed ([[Two's complement]]), it introduces the signed bit value (0s for positive numbers and 1 for negative numbers).

```
00000000 00000000 00000000 00001111 >> 2 = // 15
00000000 00000000 00000000 00000011        // 3

11111111 11111111 11111111 10000111 >> 2 = // -121
11111111 11111111 11111111 11100001        // -31
```

A single right shift divides a binary number by 2. In [[Two's complement]], the right shift always rounds up to -infinity. 
```
    00000000 00000000 00000000 01100000 >> 1 = // 96
    00000000 00000000 00000000 00110000        // 48

    11111111 11111111 11111111 11111101 >> 1 = // -3
    11111111 11111111 11111111 11111110        // -2
```


This means that `-1 / 2` is rounded to -1, not to 0. In bit representation, it would be as follows:

```
11111111 11111111 11111111 11111111 >> 1 = // -1
11111111 11111111 11111111 11111111        // -1
```

### Left and right rotation
This is similar to shifting, but instead of losing bits and adding new ones, the value of the bit rotates to one direction. Therefore, the number of 0s and 1s of the number is always constant. The right rotation is notated as `ROR` and the left rotation as `ROL`.

```
00000000 00000000 00000000 00001111 ROL 4 = // 15
00000000 00000000 00000000 11110000        // 240

00000000 00000000 00000000 00001111 ROL 4 = // 15
11110000 00000000 00000000 00000000         // -268.435.456
```

There is another special rotation, _rotation through carry_, that includes the carry bit in the rotation circle, between the first and last bit.

### More information
- [[Instruction Set Architecture of ARM#Shifter | Bit shifting in ARM assembler instructions]]

---
Planted: 2022-01-25
Last tended: 2022-01-25