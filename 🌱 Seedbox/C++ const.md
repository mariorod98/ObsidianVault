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

const int x = 10; // Correct
```

## Constant pointer
A pointer declaration can have the **const** keyword in three different places that define the behavior of the keyword.

### Pointer to const value
If we want to reference a const value by a pointer, we cannot use a pointer to non-const values (the standard pointer). We need to define a pointer (const or not) that references a const value. To do so, the **const** keyword must go before the pointer's data type.

```c++
const int value = 8;
const int another_value = 10;

int* one_pointer; // Non-const ptr that references non-const values
const int* another_pointer; // Non-const ptr that references const values

one_pointer = &value // Error: cannot convert from const
another_pointer = &value // Correct

*another_pointer = 3 // Not allowed
another_pointer = &another_value; // Correct, the pointer is not const
```

The pointer to const can also point to non-const values, but the value can't be changed from the pointer itself.

```c++
int non_const_value = 5;
const int* my_pointer;

my_pointer = &non_const_value;

non_const_value = 10; // Correct
*my_pointer = 12;     // Error: assignment of read-only variable
```

### Const pointer
A const pointer acts as a const variable. ==It must be initialized when declared and it's value cannot be changed after initialization==. However, the value that it points to can be modified. To declare a const pointer, we must use the **const** keyword after the asterisk in the pointer declaration.

```c++
int x = 5;

int* const ptr_1 = &x; // Const ptr to a non-const variable

*ptr_1 = 3; // Correct. 

int z = 2;
ptr_1 = &z; // Error: assignment of read-only variable
```

### Const pointer to a const value
A const pointer to a const value is the sum of the aforementioned uses. The pointer must be initialized when declared and neither the pointer nor the value it points to can be modified. ==It can only be dereferenced to get the value it is pointing at==.
```c++
const int x = 5;

const int* const ptr_1 = &x; // Const ptr to a const variable

*ptr_1 = 3; // Error: assignment of read-only variable. 

int z = 2;
ptr_1 = &z; // Error: assignment of read-only variable
```

---
Planted: 2022-03-24
Last tended: 2022-08-01