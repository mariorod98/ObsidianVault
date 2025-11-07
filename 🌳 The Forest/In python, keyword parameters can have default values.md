---
created: 2025-11-07
last updated: 2025-11-07
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python

# In python, keyword parameters can have default values
In this case, these parameters can be omitted in the call and they will have the default value. ==Parameters with default values must be at the end of the parameter list.==

```python
def func1(arg1 = "Hello")
	print(arg1)
	
func1() # prints "Hello"
func1("Bye") # prints "Bye"

def fucn2(arg1, arg2, arg3 = 0.5):
	return (arg1 + arg2) * arg3
	
func2(1, 2) # returns 1.5
func(1, 2, 0.2) # prints 0.6

# invalid, all params after arg2 must be optional
def func3(arg1, arg2 = False, arg3):
	# body
```


## References

## Related notes
[[In python, there are positional and keyword arguments]]