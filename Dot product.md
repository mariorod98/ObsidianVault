---
created: 2023-08-17
last updated: 2025-11-04
---

up:: [[Vectors]]
tags:: #state/seedling #on/math/geometry 

# Dot product

## The direction of two vectors using the dot product
The geometric formula for the dot product of two vectors (A and B) is:
```
dot = length(A) * length(B) * cos(angle(A,B))
```
If A and B are unitary vectors, then the geometric formula is left as
```
dot = cos(angle(A,B))
```
Therefore we can use this property to know the direction between the two vectors.

If the dot product of two unitary vectors is:
- Equal to 0, then the two vectors are orthogonal (perpendicular).
- Equal to 1, then the two vectors are facing the same direction.
- Equal to -1, then the two vectors are facing opposite directions.

## Project one vector to another

Given two vectors A and B we can project A onto B by:
```
U = B.Normalized
Projection = U * A.U
```

![[Pasted image 20240222164552.png]]