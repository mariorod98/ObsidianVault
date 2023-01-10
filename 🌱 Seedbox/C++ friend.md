up::
tags:: #state/seedling

# C++ friend

The **friend** keyword is used to grant a function or class access to private and protected members of another class. The keyword is declared in the body of the class whose members are to be accessed.

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

```cpp
class EntityManager {
	void my_func(Entity e);
	...
};

class Entity {
	...

	// Now my_func from EntityManager has access to Entity's
	// private and protected members
	friend EntityManager::my_func(Entity e);
}
```
## References
[Friend Class and Function in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/friend-class-function-cpp/)
[Friend declaration - cppreference.com](https://en.cppreference.com/w/cpp/language/friend)

---
Planted: 2023-01-10
Last tended: 2023-01-10