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


Enum values are assigned an internal int value. If no value is provided, the enum value will receive the following int from the previous value. If the first enum value is not defined, it will receive the int value of 1.

```c++
enum Directions {
	North, // Value = 1
	South, // Value = 2
	East,  // Value = 3
	West   // Value = 4
};

enum PaymentTypes {
	Metallic,     // Value = 1
	Paypal = 315, // Value = 315
	CreditCard,   // Value = 316
}
```

---
Planted: 2022-10-03
Last tended: 2022-10-03