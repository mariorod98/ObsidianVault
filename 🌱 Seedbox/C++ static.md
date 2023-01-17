up::
tags:: #state/seedling

# C++ static

Cualquier funcio pública (no static) será tratada por el compilador mediante el prolog y el epilog, para garantizar que cualquier archivo puede llavmar a la funcion
## Static in a .c
Static in C means that the variable or method is private to the file. There can exist two global variables, structs, functions, etc with the same signature that are static.

## Static in a .h
Each .c that includes that header will have a private variable with that signature.

## References

---
Planted: 2023-01-16
Last tended: 2023-01-16