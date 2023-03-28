up::
tags:: #state/seedling

# Interview questions

## Personal questions
### Describe yourself in one line

### What is your salary expectation

## Design, structures, algorithms
### What is the diamond problem in inheritance?
The diamond problem refers to the ambiguity that arises when two classes B and C inherit from a class A, and a class D inherits from both B and C. If there is a virtual method in A that is overridden by both B and C, but not overridden in D. If D calls that method, which version is called: B or C?
### What are smart pointers? Advantages and disadvantages?

### What differences does vectors and lists have? Which is better at what?

## C++

### What is the size of an empty class
An empty class has a size of 1 byte to guarantee that it has a specific address in memory.

### How to calculate the size of a class
1. First calculate the size of all the non-static attributes. Remember to consider the padding between attributes to reach 4 bytes.
2. The size of a class also includes the size of its immediate base class.
3.  Each virtual function adds 4 bytes to the vtable of the class. If the base class has this function, then it is not added again.
4. If there is virtual inheritance, then it adds 4 bytes for a pointer to the base class.

### How do we declare a constant variable in a header file? 
Before C++17, we had to declare the variable `static` in the header file and then initialize it in a cpp file.

Since C++17, we can declare and initialize a constant in a header file with the keyword `inline` to ensure that the constant is created only once in one file. Then, the linker is the responsible to link that constant in the rest of the files that use it.

### How is the memory of the program arranged?

### What is the vtable?

### What is a friend class?

### What is forward declaration?
Forward declaration is a technique used to declare a variable, function or class before its actual definition.

It is used mainly to reduce dependencies between different parts of the program and improve readability of the code. However, if not used properly it can result in errors of undefined references.

### How does a virtual function work inside a compiler?

### What is a static variable? and function?

### What are the differences between a struct and a class?

### What is the difference between a pointer and a reference?

### What is a parameter pack?

### What does rvalue and lvalue mean?

### What are the benefits of templatization?

### What is a magic number?
A magic number is a literal number inserted in an operation in the code. It is a number that, when you read the code, you don't know what that number represents.

To avoid magic numbers, you can declare const variables to give does values a readable representation. Moreover, since C++11 you can declare `constexpr` to define variables at compile-time.

## Math
### What is the dot product used for?
The dot product is the product of the magnitude of two vectors and the cosine of their angle.

For two unitary vector:
- If the dot product is greater than 0, both vectors are facing the same direction. If it is exactly 1, their angle is 0º. 
- If it is than 0, they are facing opposite directions. If it is exactly -1, their angle is 180º.
- If it is equal to 0, they are perpendicular (90º angle). 

The dot product is used in the following scenarios:
- When we want to know how close are two unitary vectors without calculating the angle (dot product is much more fast).

### Can you explain the use of sine and cosine functions in video game development, and provide an example of when you would use them?

### How would you calculate the angle between two vectors in 3D space, and why is this important in video game programming?

## Unreal
### What is the EQS and what is it used for?

## References

---
Planted: 2023-03-15
Last tended: 2023-03-15