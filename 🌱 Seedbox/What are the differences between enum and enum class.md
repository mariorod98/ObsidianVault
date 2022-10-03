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


Enu 

---
Planted: 2022-10-03
Last tended: 2022-10-03