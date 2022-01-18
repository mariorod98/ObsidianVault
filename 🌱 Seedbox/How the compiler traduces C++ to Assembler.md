---
tags: state/seedling on/assembler on/cpp
---

# C++ to Assembler
Para realziar operqaciones aritmeticas, utilizar el int (tamaño de palabra del procesador) será mas eficiente. Si realizamos operaciones artimeticas sobre un short o un chart, el procesador debe hacer operaciones extra.

    unsigned char a = 254; 
    a += 100; // a = (254 + 100) % 255 = 99

    mov r0, #259
    add r0, r0, 100
    and r0, #0xFF

Como el unsigned char son 8 bits y el registro son 32, al realizarse una operacion sobre un char deben ponerse todos los bits 9-31 a 0 para mantener el valor en el rango 0-254. Para ello se realiza un and con 0xFF, que pone los primeros 24 bits a 0 y los últimos 8 a 1.


---
Planted: 2022-01-18
Last tended: 2022-01-18