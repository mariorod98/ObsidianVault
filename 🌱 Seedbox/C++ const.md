up:: [[🖥️ C_C++]]
tags:: #state/seedling #on/cpp

# C++ const

## Constant variable
When a variable is preceded by the **const** keyword, it specifies that the variable's value is constant and tells the compiler to prevent the program from modifying it.
- The variable cannot be left un-initialized at the time of the assignment.
- It cannot be assigned value anywhere in the program.

```c++
const int x; // Error: uninitialized const
x = 10;      // Error: assignment of read-only variable
```

## Constant pointer
A pointer declaration can have the **const** keyword in three different places that define the behavior of the keyword.

### When the pointer variable points to a const value
```c++
const int* my_pointer;
```

---
Planted: 2022-03-24
Last tended: 2022-08-01