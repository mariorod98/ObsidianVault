up: [[🖥️ C_C++]]
tags: #state/bud #on/c/pointers

# What is a pointer?
A pointer is a reference to a memory address that stores a value. In practice, a pointer is treated as if it were an integer. Even though they are the same, there is not an implicit [[casting]] between integers and pointers. You must explicitly cast it as a sanity check. This casting has no cost, as it doesn't modify the value in any way.
```cpp
char* p = (char*) 1111; -> Doesn't involve WR/RD
*p = 1; <-> p[0] = 1; -> WR
a = *p; <-> a = p[0]; -> RD
```

## Pointer arithmetic
Pointers can only be added or subtracted. When you add/subtract a value `a` to a pointer, you are adding/subtracting `a` times the size of the object reserved in the pointer.

```cpp
short* p = (...) 1000000; \\ size of short = 2
p++;    \\ p = 1000000 + sizeof(short) -> p = 1000002;
p += 2; \\ 1000000 + 2 * sizeof(short) -> p = 1000004;
```

## Pointers and arrays
An array contains a special pointer that points to the first direction of the array ([0]). This pointer cannot be modified in any way, either by adding/subtracting or by assigning a new value to the pointer. The only use of this pointer is by [[dereferencing]] it.
```cpp
short ar[100]; 
short* p;
p = &ar[2]; \\ Obtains the elements address. No dereferencing is involved.
p = ar + 2; \\ Does the same as the previous line
```

## Pointers and 2D arrays
Pointers to 2D arrays are barely used because you can't use them as a parameter in functions (the compiler must know the number of rows and columns in order to use the array). Therefore, a 1D array is used to simulate 2D arrays. The declaration and access of a value of a 2D array is done as follows:

```cpp
char m[w \* h]; // declaration
m[x + y \* w];  // access
```

---
Planted: 2022-01-16
Last tended: 2022-01-16