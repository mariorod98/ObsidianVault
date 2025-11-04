---
created: 2023-08-07
last updated: 2025-11-04
---

up::
tags:: #state/seedling  #on/programming/clean_code 

# How to name code correctly

## Choose specific words

When defining classes, methods or variables, try to be as specific as possible (within a certain limit). 

**Bad examples**
- A class `BinaryTree` that has a method `Size`. What does `Size` refer to? The number of nodes? The height of the tree? The size in memory?
- The following variable `float distance = (TargetPos - MyPos).Length()`. If I use different distances in the function, how do I identify which distance am I referring to? A better name would be `distanceToTarget`. 

## Avoid generic names like tmp and retval
Try to use names that describe the entity's value or purpose. It is tempting to use generic names for variables with a reduced scope and lifetime but they do not pack much information and make the code harder to read.

There are extreme cases where the generic name is valid if the lifetime of the variable is really small. For example, the swapping of two variables:

```
if(right < left) {
	tmp = right;
	right = left;
	left = tmp;
}
```

## Prefer concrete names over abstract names
Here are some general tips to be more concrete:
- Use measurements in the name. Instead of elapsed, use `elapsed_ms`. Instead of distance, use `distance_m`.
- Attach extra information to the name. If you have a variable `id` that stores an hexadecimal code, maybe name it `hex_id` so that you always remember the format of the id.
- Avoid acronyms and abbreviations that are not perfectly clear. `AI` is clear that comes from Artificial Intelligence and `str` is comes from string, but `BEManager` does not provide any information.
- Remove unneeded words. `ConvertToString` can be renamed `ToString`, `DoLoop` can be changed to `Loop`.

## Use name formatting to convey meaning
The way you use underscore, dashes and capitalization can also pack more information in a name. This makes the code easier to read.
- Having constants and macros be in all caps.
- Starting class and method names with upper case and variables with lowercase.
- Starting member variables with a m_.