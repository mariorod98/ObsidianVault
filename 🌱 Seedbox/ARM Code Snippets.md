---
tags: state/seedling
---

# ARM Code Snippets

**Read the value stored in a pointer**
``` c
// C code
SeedParticles(unsigned short* screen) {
    unsigned short x = *screen;
}

```
``` armasm
; Assembly code
SeedParticles:
  ldrh r1,[r0, #0] ; x = *screen
```

**Read the value of a member of a struct**
```c
// C code
struct Snake {                 // Size Pos
    Slabs* slabs;              //  4B  0
    unsigned short len;        //  2B  4
    unsigned short head_slab;  //  2B  6
    int speed_x;               //  4B  8
    int speed_y;               //  4B  12
}                              // 16B

void UpdateSnake(Snake* snake) {
    snake->len = 0;
    int x = snake->speed_x;
}
```
```armasm
; Assembly code
UpdateSnake:
    mov  r1,#0      ; r1 = 0
    strh r1,[r0,#4] ; snake->len = r1
    ldr  r1,[r0,#8] ; x = snake->speed_x
    
```
**Read the value from an array**

---
Planted: 2022-05-10
Last tended: 2022-05-10