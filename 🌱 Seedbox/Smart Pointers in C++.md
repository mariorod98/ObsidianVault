up:: [[🖥️ C_C++]]
tags:: #state/seedling #on/cpp

# Smart Pointers in C++
## Concept of ownership
When we talk about the *ownership* of a resource, we are talking about who is responsible for the cleanup of that resource once it stops being used. In other words, the **owner** of a resource is the responsible of **deleting** the resource from memory.

C++ base pointers do not operate with the concept of ownership, so the programmer is the responsible of designing the owner of a resource and making sure the owner destroys that result. In complex projects, this could lead to potential memory leaks and bugs difficult to debug.

To solve this problem, **smart pointers** were introduced in C++11. Smart pointers are manage the ownership of a resource, freeing the programmer from that task. Now, ==the programmer must understand when to use smart pointers and which one to use==.

There are three key concepts about ownership and smart pointers:
- **No ownership at all.** The smart pointer cannot delete the object, because it doesn't own it.
- **Transfer of ownership.** Only one smart pointer can ever point to the same object at the same time. If the smart pointer is returned from functions, the ownership is transferred to the returned smart pointer.
- **Share of ownership.**  Multiple smart pointers can point to the same object at the same time. The last owner will be the responsible to free the resource.

## Unique pointers
A **unique_ptr** is a smart pointer that limits the ownership of a resource to a single entity. The entity is deleted when the scope of the unique_ptr ends. Only one unique_ptr can point to the same resource, so the copy and assignment operations are not implemented.

```c++
class Entity {
public:
	unique_ptr<
}
```

### Passing ownership to other objects

### when to use unique pointers

## Shared pointer
## Weak pointer
## Auto pointer


---
Planted: 2022-11-08
Last tended: 2022-11-08