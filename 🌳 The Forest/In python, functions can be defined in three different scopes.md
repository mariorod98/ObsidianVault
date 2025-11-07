---
created: 2025-11-07
last updated: 2025-11-07
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python

# In python, functions can be defined in three different scopes
Functions are local to the scope they are declared: 
- **If declared in global scope**, they can be accessed everywhere in the file.
- **If declared inside a class**, they are member functions of the class.
- **If declared inside another function**, they are private to the parent function and only accessed by it. 

```python
def global_function():
	print("I'm a global method")
	
class MyClass:
	# every class method must have self as frst parameter
	# private methods start with two underscores
	def __private_method(self):
		print("I'm a private method")
		
	# protected methods start with one underscore
	def _protected_method(self):
		print("I'm a protected method")

	# public methods start with no underscores
	def public_method(self):
		print("I'm a public method")
		
def my_func(value):
	# not accessible from outside
	def plus_2(value):
		return value + 2
		
	return plus_2(value)
```

## References
[Python Nested Functions](https://stackabuse.com/python-nested-functions/)

## Related notes
[[In python, you can reference global and nonlocal variables inside functions]]