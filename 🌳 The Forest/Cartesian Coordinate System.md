up:: [[📐 Geometry]]
tags:: #state/bud #math/geometry

# Cartesian Coordinate System
A $n$D Cartesian Coordinate System is a space defined by two pieces of information:
- The *origin*, a nD point that defines the center of the coordinate system.
- $n$ axes, usually perpendicular to each other.

in theory, this coordinate space is **boundless**, all the axes extend potentially infinitely.

## How to use it
A coordinate space is a framework for specifying location precisely and mathematically. To define the location of  a point in a Cartesian coordinate space, we use Cartesian 
coordinates. 

## 2D coordinate system
In 2D, two numbers are used to specify a location, $x$ and $y$. Each number is the signed distance to one of the axes. The $x$ coordinate designates the signed distance from the point to the $y$-axis, measured along a line parallel to the $x$-axis. Likewise, the $y$ 
coordinate designates the signed distance from the point to the $x$-axis, measured along a line parallel to the $y$-axis.

![[Pasted image 20250705231710.png]]

## 3D coordinate system
In 3D, any pair of axes defines a plane that contains two axes and is perpendicular to the third axis (the plane containing x- and y-axes is the $xy$ plane, etc). We can consider any of these planes a 2D Cartesian coordinate space in its own right.

![[Pasted image 20250705231723.png]]

Unlike 2D CS, all 3D spaces are **not** equal. There are exactly two distinct types: *left-handed* CS and *right-handed* CS. If two coordinate spaces have the same handedness, then they can be rotated such that axes are aligned. If they are opposite handedness, then this is not possible.

==Any left-handed coordinate system can be transformed into a right-handed coordinate system or viceversa. The easiest way to do this is by swapping the positive and negative ends of one axis.==

## References
[Cartesian Coordinate Systems - 3D Math Primer for Graphics and Game Development](https://gamemath.com/book/cartesianspace.html)

---
Planted: 2025-07-05
Last tended: 2025-07-05