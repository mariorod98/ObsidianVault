up:: [[🖥️ C_C++]]
tags:: #state/bud #on/cpp

# C++ const

## Constant variables
When a variable is preceded by the **const** keyword, it specifies that the variable's value is constant and tells the compiler to prevent the program from modifying it.
- The variable cannot be left un-initialized at the time of the assignment.
- It cannot be assigned value anywhere in the program.

```c++
const int x; // Error: uninitialized const
x = 10;      // Error: assignment of read-only variable

const int x = 10; // Correct
```

## Constant pointers
A [[A pointer is a reference to a memory address|pointer]] declaration can have the **const** keyword in three different places that define the behavior of the keyword.

### Pointer to const value
If we want to reference a const value by a pointer, we cannot use a pointer to non-const values (the standard pointer). We need to define ==a pointer (const or not) that references a const value==. To do so, the **const** keyword must go before the pointer's data type.

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

## Constant objects
As any other variable, objects can also have the **const** keyword. ==When an object is const==, it needs to be initialized at the time of declaration  (with the constructor) and ==its state (the values of its attributes) cannot be change==. 

```c++
class Point {
	int x, y;
}

...

const Point my_point = new Point();
my_point.x = 10;  // Error: assignment of read-only variable
```

## Constant methods
To ensure that a constant object cannot be modified, it can only use  constant methods. ==These methods must not modify the state of the object, therefore its attributes are read-only==.

==Constant objects can only call constant methods, therefore, when defining a new method, it is important to add the keyword if it is appropriate.==

```c++
class Point {
	int x, y;

	void Add(int x, int y) {
		this.x += x;
		this.y += y;
	}

	int GetX() {
		return x;
	}

	int GetY() const {
		return y;
	}

	int SetX(int x) const {  
		this.x = x; // Error: a const method cannot modify the state of the object
	}  
}

...

const Point my_point = new Point();
my_point.Add(5, 4);  // Error: the method modifies the state of the object

my_point.GetX();     // Error: even though it doesn't modify the state, the method must be declared const

my_point.GetY();    // Correct.

```

## Constant function parameters
The parameter of a function can be declared const to ensure that it will not be modified.

```c++
void my_func(const int a) {
	a = 1; // Error: assignment of read-only variable
}
```

## Const function return
When the return type of a function is declared const, the variable that stores the returned value must be const. This means that the variable must be declared when calling the function and that it will not be modified.

```c++
class Point {
	int x, y;
}

const Point my_func(int x, int y) {
	return new Point(x, y);
}

...

Point p;
p = my_func(1, 2);  // Error: cannot assign const Point to Point variable

const point p2;      // Error: const variables must be initialized
p2 = my_func(1, 2);

const Point p3 = my_func(1, 2);  // Correct.
```


## References
[9.8 — Pointers and const – Learn C++](https://www.learncpp.com/cpp-tutorial/pointers-and-const/)
[Const keyword in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/const-keyword-in-cpp/)

---
Planted: 2022-03-24
Last tended: 2022-08-02