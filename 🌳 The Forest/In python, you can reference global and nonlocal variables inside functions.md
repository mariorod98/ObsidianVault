---
created: 2025-11-07
last updated: 2025-11-07
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python

# In python, you can reference global and nonlocal variables inside functions
Functions can declare local variables inside their own scope. **These variables can have the same name as variables in global or other scopes**. If a local variable is created (as in, assigned a value) with the same name as a global variable, the function will use and modify only the local variable.

==To use a global variable inside a function, we use the keyword `global`.==
==To use a variable from the parent function scope, we use the keyword `nonlocal`==

```python
x = 10

def func1():
	# access global x, prints 10
	print(x)
	
def func2():
	# creates local variable
	x = 2
	# prints 2, global x unchanged
	print(x) 
	
def func3():
	# indicates that we are using a global variable
	global x
	# changes global variable
	x = 3
	# prints 3, global x is now 3
	print(x)
	
	
def func4():
	y = 5
	def private_func1():
		# access nonlocal var, prints 5
		print(y) 
		
	def private_func2():
		# creates local variable
		y = 8
		# prints 8, nonlocal y unchanged
		print(y)
		
	def private_func3():
		# indicates that we are using a variable from parent function
		nonlocal y
		# changes nonlocal variable
		y = 8
		# prints 8, nonlocal y is now 8
		print(y)
```

## References

## Related notes
[[In python, functions can be defined in three different scopes]]