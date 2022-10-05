up::
tags:: #state/seedling #on/cpp

# What are the differences between enum and enum class

## What is an enum?
An **enum** (or enumeration) is a user-defined data type which can be assigned a value from a limited range. These values are defined by the programmer at the time of declaring the enumerated type.

Enums are often used to create categories and non quantitative values with restricted values. For example:
- Days of the week.
- States of a FSM.
- Types of enemies.
- Compass directions.
- Type of payment.
- Options.

```c++
enum DaysOfWeek {
	Monday,
	Tuesday,
	Wednesday,
	Thursday,
	Friday,
	Saturday,
	Sunday
};

int main() {
	DaysOfWeek today = Monday;
}
```

Enum values are assigned an internal int code. If no code is provided, the enum value will receive the following number from the previous code. If the first enum value has no code assigned, it will receive the int code of 0.

```c++
enum Directions {
	North, // Code = 1
	South, // Code = 2
	East,  // Code = 3
	West   // Code = 4
};

enum PaymentTypes {
	Metallic,     // Code = 1
	Paypal = 315, // Code = 315
	CreditCard,   // Code = 316
};
```

This means that an enum can be assigned and compared to any int, even other enums.

```cpp
enum Directions {
	North, // Value = 1
	South, // Value = 2
	East,  // Value = 3
	West   // Value = 4
};

enum PaymentTypes {
	Metallic,     // Code = 1
	Paypal = 315, // Code = 315
	CreditCard,   // Code = 316
};

int main() {
	Directions dir = North;
	bool isNorth = dir == 1; // True
	dir = 3; // dir = East

	PaymentTypes payment = Metallic;
	bool isMetallic = payment == North; // True
}
```

### Problems of the enum type
**Two enums cannot share the same names** because of the soft typing of its values.

```cpp
enum Gender {Male, Female};
enum Gender2 {Male, Female}; // This will throw a redeclaration error
```

**No variable can have a name already used in some enumeration.**

```cpp
enum Gender{Male, Female};
int Male; // This will thro a redeclaration error
```

**Enums are not type-safe.**

```cpp
enum Directions {
	North, // Value = 1
	South, // Value = 2
	East,  // Value = 3
	West   // Value = 4
};

enum PaymentTypes {
	Metallic,     // Code = 1
	Paypal = 315, // Code = 315
	CreditCard,   // Code = 316
};

int main() {
	Directions dir = North;
	PaymentTypes payment = Metallic;
	
	bool isMetallic = North == Metallic; // True
}
```

## What is an enum class?
The **enum class** (or scoped enum) was introduced in C++11 to solve the aforementioned problems. It makes enumerations both **strongly typed and strongly scoped**. 

Class enums don't allow implicit conversion to int and doesn't compare enumerators to different enumerators.

```cpp
enum Directions {
	North, // Value = 1
	South, // Value = 2
	East,  // Value = 3
	West   // Value = 4
};

enum PaymentTypes {
	Metallic,     // Code = 1
	Paypal = 315, // Code = 315
	CreditCard,   // Code = 316
};

int main() {
	Directions dir = North;

	int North = 10; // class enum values can be used as variable names
	
	dir = 3; // Error, implicit conversion
	dir = Directions(3) // Correct, explicit conversion
	
	int value = dir; // Error, implicit conversion
	value = int(dir); // Correct, explicit conversion

	PaymentTypes payment = Metallic;
	bool isMetallic = payment == North; // True
}
```

---
Planted: 2022-10-03
Last tended: 2022-10-03