up::
tags:: #state/seedling

# C++ static
The **static** keyword can be used along with function and variable declarations. The meaning of the keyword varies between variables and functions.

## Static variables
When a variable is declared as **static**, ==space for the variable is allocated for the lifetime of the program==.

### Static variable in a function
If a static variable is declared in a function, ==only that function can access the variable==. However, **the memory (and value) of the variable is preserved between function calls**.

Static variables declared in functions are initialized during the first call of the function.

### Static variables in classes
As a static variable is only allocated once in memory, a static variable in a class is shared by all the objects of that class.

The static variable must be initialized outside of the class scope. Usually, it is done in the cpp file that contains the class definitions.

### Static class object
As with other types, objects can also be declared as static. A static object has the scope of the entire execution of the program. The constructor is called at the beginning of the main function and the destructor is called at the end.

## Static functions

### Inside a class
When a function is declared as static, that function ==can be called without an instance of a class==. This function **cannot access non-static members/functions of the class**.

### Outside of a class

Cualquier funcio pública (no static) será tratada por el compilador mediante el prolog y el epilog, para garantizar que cualquier archivo puede llavmar a la funcion
## Static in a .c
Static in C means that the variable or method is private to the file. There can exist two global variables, structs, functions, etc with the same signature that are static.

## Static in a .h
Each .c that includes that header will have a private variable with that signature.

## References

---
Planted: 2023-01-16
Last tended: 2023-01-16