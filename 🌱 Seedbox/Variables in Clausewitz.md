up:: [[⚔️ Cluasewitz Engine]]
tags:: #state/seedling #on/clausewitz 

# Variables in Clausewitz

Variables are persistent values that are either associated with a specific game object.

## Setup of a variable
```
set_variable = {
	which = myCountingVariable
	value = 0
}
```

## Modify a variable
To modify a variable, you can use the following [[Effects in Clausewitz|effects]]:
- `change_variable` to add.
- `subtract_variable` to subtract.
- `divide_variable` to divide.
- `multiply_variable` to multiply.

```
# immediate section of an event
immediate = {
	change_variable = {
		which = myCountingVariable
		value = 1
	}
}
```

## Check a variable
To check a variable, you can use the [[Effects in Clausewitz|effect]] `check_variable`.

```
# checks if the variable is >= 5
check_variable = {
	which = myCountingVariable
	value = 6
}

# checks if the variable is == 5
check_variable = {
	which = myCountingVariable
	value = 5
}
NOT = {
	check_variable = {
		which = myCountingVariable
		value = 6
	}
}
```

## Variables in different games
### Europa Universalis 4
Variables operate in *country* and *province* [[Scopes in Clausewitz |scopes]], and in both [[Effects in Clausewitz|effect]] and [[Triggers in Clausewitz|trigger]] contexts, although the commands and conditions used in either context differ.

==Values can not be used as right sided arguments (in an effect section for instance) except for religion and culture.==




---
Planted: 2022-12-16
Last tended: 2022-12-16