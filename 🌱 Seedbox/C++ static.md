up::
tags:: #state/seedling

# C++ static
The **static** keyword can be used along with function and variable declarations. The meaning of the keyword varies between 

Cualquier funcio pública (no static) será tratada por el compilador mediante el prolog y el epilog, para garantizar que cualquier archivo puede llavmar a la funcion
## Static in a .c
Static in C means that the variable or method is private to the file. There can exist two global variables, structs, functions, etc with the same signature that are static.

## Static in a .h
Each .c that includes that header will have a private variable with that signature.

## Static variables
When a variable is declared as static, space for the function is allocated for the lifetime of the program.

### Static variables in classes
As a static variable is only allocated once in memory, a static variable in a class is shared by all the objects of that class.

The static variable must be initialized outside of the class scope. Usually, it is done in the cpp file that contains the class definitions.

### Static class object
As with other types, objects can also be declared as static. A static object has the scope of the entire execution of the program. The constructor is called at the beginning of the main function and the destructor is called at the end.

## Static functions

## References

---
Planted: 2023-01-16
Last tended: 2023-01-16