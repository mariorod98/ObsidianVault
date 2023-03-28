up::
tags:: #state/seedling

# Interview questions

## Personal questions
### Describe yourself in one line

### What is your salary expectation

## Design, structures, algorithms
### What is tech debt?
Tech debt is a term that defines when a developing team prioritizes speeding up the development of features over creating scalable and maintainable features. The consequences of this behaviour is that eventually you will have to refactor that code, wasting more time that it would have taken if you had written the feature properly to begin with.

### What is the diamond problem in inheritance?
The diamond problem refers to the ambiguity that arises when two classes B and C inherit from a class A, and a class D inherits from both B and C. If there is a virtual method in A that is overridden by both B and C, but not overridden in D. If D calls that method, which version is called: B or C?

C++ solves this problem by not allowing virtual classes 

### What differences does vectors and lists have? Which is better at what?
Vectors store their elements in sequence in memory. To iterate through the vector, you just have to pass to the next position in the memory.

A list does not store all its elements in sequence, they are scattered through the memory. To traverse the elements, the list stores, with each element, a pointer to the memory position of the next element.

Vectors are faster when iterating over elements and when the number of inserts and deletes are not high.

Lists are faster if you do not have to iterate the entire list and when you are constantly inserting and deleting elements.

## C++
### What are smart pointers? Advantages and disadvantages?
Smart pointers are a wrapper class used to manage the heap memory in a safe way that reduce memory leaks and memory related bugs. 

Smart pointers work by destroying the object they point to whenever the pointer life ends, in other words, when they go out of scope.

The disadvantage is that smart pointers are heavier in memory than simple pointers.

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

We use dot product when we want to know how close are two unitary vectors without calculating the angle (dot product is much more fast). 

The dot product is used in the following scenarios:
- If the player is inside enemy vision.
- To make one way triggers.
- To prompt a player action if they are facing the target.

### Can you explain the use of sine and cosine functions in video game development, and provide an example of when you would use them?

### How would you calculate the angle between two vectors in 3D space, and why is this important in video game programming?

If I need the specific value of the angle between both vectors, I would just use the angle equation of `arccos((a . b) / (|a|*|b|))`.

However, if I just need to now if they are facing the same direction or opposite direction, I would use the dot product, as it gives this information with much less computational cost.
## Unreal
### What is the EQS and what is it used for?

## References

---
Planted: 2023-03-15
Last tended: 2023-03-15