up::
tags:: #state/seedling

# C++ friend

The **friend** keyword is used to grant a function or class access to private and protected members of another class. The keyword is declared in the body of the class whose members are to be accessed.

Some key features are:
- Friendship is not transitive (a friend of a friend is not your friend).
- Friendship is not inherited (your friend's children are not your friends).


**Example with friend class**
```cpp
class EntityManager {
	...
};

class Entity {
	...

	// Now EntityManager can have access to Entity's
	// private and protected members
	friend class EntityManager;

	// Can also be declared like this since C++11
	// friend EntityManager;
}
```


**Example with friend function**
```cpp
class EntityManager {
	void my_func(Entity e);
	...
};

class Entity {
	...

	// Now my_func from EntityManager has access to Entity's
	// private and protected members
	friend void EntityManager::my_func(Entity e);
}
```
## References
[Friend Class and Function in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/friend-class-function-cpp/)
[Friend declaration - cppreference.com](https://en.cppreference.com/w/cpp/language/friend)

---
Planted: 2023-01-10
Last tended: 2023-01-10