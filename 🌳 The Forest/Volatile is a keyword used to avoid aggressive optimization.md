up: [[🖥️ C_C++]]
tags: #state/bud #on/cpp


# Volatile is a keyword used to avoid aggressive optimization

**Volatile is a keyword used to tell the compiler to avoid aggressive optimization involving that variable.** It might be usable in some instances where the value of the variable may be changed in a way that the compiler is not aware of. For example, consider the code:

```cpp
int some_int = 100;
while(some_int == 100) {
	// code
}
```

If the compiler detects that the value of the variable ``some_int`` never ever changes, it may optimize the while loop to something like: ``while(true)``. This may be undesirable if the variable ``some_int`` is modified outside the program (via hardware).

==The volatile keyword is hardware dependent, so it's use and applications may vary between compilers.==

---
Planted: 2022-04-28
Last tended: 2022-07-06