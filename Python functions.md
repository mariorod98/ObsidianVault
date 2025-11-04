## Function scope
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

## Variable Scope
Functions can declare local variables inside their own scope. **These variables can have the same name as variables in global or other scopes**. If a local variable is created (as in, assigned a value) with the same name as a global variable, the function will use and modify only the local variable.

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

## Return value
Python functions always return a single object. It is `None` if there is no return statement in the method. If the return statement is followed by multiple values, it returns a `tuple` with the values.

Functions can also return other functions, even inner ones.

## Parameters
### Parameters by reference vs value
In Python, parameters are passed by reference, modifying their internal state in a function will modify the object outside the function. However, assigning them inside a function will not modify them outside, just reassign the variable to a new local object.

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

### Call functions with parameter list or dictionary


### Optional parameters
Functions can have parameters with default values. In this case, these parameters can be omitted in the call and they will have the default value.

==Parameters with default values must be at the end of the parameter list.==
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

### Parameter expansion


## References
https://stackabuse.com/python-nested-functions/
https://www.geeksforgeeks.org/python/access-modifiers-in-python-public-private-and-protected/
