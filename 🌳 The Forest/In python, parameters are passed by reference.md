---
created: 2025-11-07
last updated: 2025-11-07
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python 

# In python, parameters are passed by reference
In Python, parameters are passed by reference, modifying their internal state in a function will modify the object outside the function. ==However, assigning them inside a function will not modify them outside, just reassign the variable to a new local object==.

```python
def append(to_modify, value):
	# list passed by reference, modifies the nonlocal object
	to_modify.append(value)
	
my_list = [1, 2]
append(my_list, 3)
print(my_list) # prints [1, 2, 3]

def reassign(old, new):
	old = new # reasigning variable, now it is local
	print(old)
	
my_list = [1, 2]
my_other_list = [3, 4]

reassign(my_list, my_other_list) # prints [3, 4]
print(my_list) # prints (1, 2)
```

## References

## Related notes