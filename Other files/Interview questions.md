up::
tags:: #state/seedling

# Interview questions

## Personal questions
### Describe yourself in one line

### What is your salary expectation

### What are your strengths and weaknesses?

### What projects have you done related to this position?

When I was studying Computer Science I chose the Artificial Intelligence specialization where I learned multiple techniques such as multi agent systems, machine learning and genetic algorithms. I know the theory and basis of all these techniques and I have developed projects for some of them.

Currently, I am working on multiple projects with a focus on new AI techniques. For example, I am implementing the Wave Function Collapse algorithm to procedurally generate an hexagonal grid world. I am also making a stealth game with enemy agents that have the basic behaviour of these types of enemies: patrolling, searching for the player, communicating between agents, etc.

Moreover, I am also developing a multiplayer game in Unreal Engine where you have to escape a labyrinth. The enemy AI in that game is done with Behaviour Trees and the perception system that Unreal provides.

### What makes a good AI programmer?

An good AI programmer is someone that needs to have great problem-solving skills. Developing realistic and engaging AIs in videogames is a complex problem where you have to be creative and think out of the box to come up with innovative solutions.

They must also embrace the iterating process, as AI systems require a lot of fine-tunning and refining the algorithms, which is a long process with a lot of iteration and backtracking.

Finally, I think that they must be constantly researching and learning. Artificial Intelligence is one of the fields that is constantly changing and evolving. Take for example the breakthrough of ChatGPT. There is always new techniques to learn and new papers to consult that could prove useful in the future.

### What responsibilities do you expect from the position?

### How do you ensure you write quality code?
I try to be as consistent as possible with the code I write and I take pride in creating code that is functional, optimized and easily understandable.

For me, quality code must be:
- Easy to read and understand by a stranger at first glance, with plenty of useful comments and following clean code guidance.
- Whenever I make a system, class or function, I try to make it as atomically as possible. They must perform just one task and only that task. They also have to be.
- I also try to avoid increasing the technical debt of my code. Stopping for a moment, designing and planning my code before jumping to write tends to produce more lasting and manageable code.

### How do you approach debugging an AI algorithm when it's not performing as expected?

Whenever I have to track and solve a bug. The first thing I do is try to replicate that bug. If it is replicable, then I can determine what are the conditions needed for the bug to happen and the task becomes much easier.

If it is not replicable, as sometimes happens when debugging AI, I try to figure out how the bug can be related to a specific system or entity.

When I have sorted out where the bug might be happening, I use debugging tools to follow the process until I get to the bug. Using specific tools for AI debugging is quite helpful here, but if none are available, a simple debugger where I can put breakpoints and watch the variables' states is enough.

In my experience, debugging AI systems tends to be a slow and sometimes tedious task that requires a lot of try and error. So it is better to plan ahead and have a consistent methodology.

### Can you give an example of how have you optimized an AI algorithm to improve its performance?

I am currently working in the procedural generation of a grid world using the Wave Function Collapse algorithm. It is an algorithm that generates a grid base on adjacency constraints.

### What are your plans for the near future? And far future?

### Why do you like AI programming?

### What inspired you to pursue a career in videogames programming?

### How would you describe your approach to problem-solving?

### Can you walk me through your experience with game engines such as Unity or Unreal?

### What programming languages are you most comfortable with and how proficient are you with them?

### Have you ever developed a game from start to finish? Can you describe the process and any challenges you faced?

### How do you approach working with a team of game developers? What strategies do you use to ensure effective collaboration?

### How do you stay up-to-date with the latest trends and advancements in game programming? Do you participate in any online communities or attend any industry events?

### Can you tell me about a particularly challenging project you've worked on and how you overcame any obstacles?

### How do you ensure that the games you develop are optimized for performance and can run on a variety of hardware platforms?

## Design, structures, algorithms
### What is tech debt?
Tech debt is a term that defines when a developing team prioritizes speeding up the development of features over creating scalable and maintainable features. The consequences of this behaviour is that eventually you will have to refactor that code, wasting more time that it would have taken if you had written the feature properly to begin with.

### What is the diamond problem in inheritance?
The diamond problem refers to the ambiguity that arises when two classes B and C inherit from a class A, and a class D inherits from both B and C. If there is a virtual method in A that is overridden by both B and C, but not overridden in D. If D calls that method, which version is called: B or C?

C++ solves this problem with the `virtual` inheritance. Declaring a parent class as `virtual` ensures that it is only inherited once, even if that class is found multiple times in the inheritance tree.

### What differences does vectors and lists have? Which is better at what?
The main differences between both containers are:

**Memory allocation**
A vector allocates its elements in a contiguous block of memory, while lists use a linked list of nodes that do not need to be contiguous in memory.

**Random access**
Due to this form of allocation, vectors support random access to elements, as it knows the memory direction of the first element and the size of the element, it can calculate the memory direction of the element in any given position.

Lists, on the other hand, do not support random access. To access a certain element, you have to iterate all the list up to that element.

**Insertion and deletion**
Insertion and deletion in a list is trivial, you just have to create or free the memory of the element and adjust the pointer of the neighboring nodes.

However, these operations in a vector are much slower, as you have to move all the elements after the inserted or deleted position. Moreover, if the number of elements exceeds the vector's capacity, you have to allocate new memory and copy all the current elements to their new location.

**Size**
Vector elements are the size of the stored element, while list elements have  a bigger size due to having to store the extra pointers. The size will depend if it is a single or double linked list. In C++ it is a double linked list.

## C++
### What are smart pointers? Advantages and disadvantages?
Smart pointers are a wrapper class used to manage the heap memory in a safe way that reduce memory leaks and memory related bugs. 

Smart pointers work by destroying the object they point to whenever the pointer life ends, in other words, when they go out of scope.

The disadvantage is that smart pointers are heavier in memory than simple pointers.

C++ uses three types of smart pointers:
- unique_ptr. Manages the ownership of an object. It is the only owner the object can have. Whenever the unique pointer goes out of scope, the object is destroyed.
- shared_ptr. Allows multiple pointers to manage the same object. Inside, it has a counter of all the references to this object. When a new shared pointer points to the object, the counter is incremented and when a shared pointer pointing to the object goes out of scope, the counter is reduced. When the counter reaches 0, the object is not referenced by any pointer and it is deleted.
- weak_ptr. A pointer used along with shared_ptr to share a pointer to an object. However, this pointer does not increment or reduce the counter of the smart pointer. It is only used to provide a weak reference to the object. It is used to safely access object that may or may not be deleted at the time of the access.

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

### What is a virtual function?

### How does a virtual function work inside a compiler?

### What is the vtable?

### What is a friend class?
In C++ the `friend` keyword is used to declare a function or class that is friend with another class. This friend function/class can access any protected and private method or attribute of the class. 

The `friend` declaration is not transitive and it is not inherited.

### What is forward declaration?
Forward declaration is a technique used to declare a variable, function or class before its actual definition.

It is used mainly to reduce dependencies between different parts of the program and improve readability of the code. However, if not used properly it can result in errors of undefined references.

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