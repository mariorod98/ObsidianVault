up::
tags:: #state/seedling #math/geometry #math/algebra

# Vectors
In linear algebra, a vector is just an array of numbers of n dimension. We say that the *dimension* of a vector is the number of elements in this array. A 1D vector is known as a [scalar].

In geometry, ==a *vector* is a geometric object that has magnitude and direction.==  It is represented by an arrow, the magnitude is the length of the arrow and the direction is where in the space coordinate is it pointing towards.

## Properties of vectors
### The zero vector
For any set, the *additive identity* of the set is the element *x*, such that for all *y* in the set, $y+x=y$

For the set of vectors of a particular dimension, the additive identity element is the so-called "zero-vector" of that dimension, which has zeros in every position.

$\mathbf{0}=\left[\begin{array}{c}0 \\ 0 \\ \vdots \\ 0\end{array}\right]$

The zero vector is the only vector with a magnitude of zero. For any other magnitude, there are an infinite number of vectors of that magnitude.

The zero vector express the concept of "no displacement".

## Vector operations
### Negating a vector
For any set, the *additive inverse* of $x$, denoted by $-x$, is the element that yields the additive identity of that set (zero) when added to $x$. Put simply: $x+(-x)=0$.

**Algebra rules**
To negate a vector of any dimension, negate each component of the vector.
$-\left[\begin{array}{c}a_1 \\ a_2 \\ \vdots \\ a_n\end{array}\right] = \left[\begin{array}{c}-a_1 \\ -a_2 \\ \vdots \\ -a_n\end{array}\right]$

**Geometric interpretation**
Negating a vector results in a vector of the same magnitude but opposite direction.

### Vector multiplication with a scalar
The result of a multiplication between a vector and a scalar is a vector that is parallel with the original vector, except with a different length and possibly opposite direction.
TODO: FINISH SECTION

### Vector addition and subtraction
TODO: FINISH SECTION

### Vector magnitude
The magnitude of a vector is also known as the *length* or *norm* of the vector.

**Algebra rules**
In algebra, the magnitude of a vector is the square root of the sum of the squares of the components of the vector. Thus, it is a **nonnegative scalar quantity**.

$\|\mathbf{v}\|=\sqrt{\sum_{i=1}^n v_i^2}=\sqrt{v_1^2+v_2^2+\cdots+v_{n-1}^2+v_n^2}$.

**Geometric interpretation**
For any vector $v$ in 2D, we can form a right triangle with $v$ as the hypotenuse.
![[{D767260E-A410-4CCA-8F6E-1D6A52532C0E}.png]]
The Pythagorean theorem states that for any triangle, the square of the length of the hypotenuse is equal to the sum of the squares of the length of the two sides.

$\|\mathbf{v}\|^2=v_x^2+v_y^2$

Then, by taking the square root in both sides, we get that 
$\|\mathbf{v}\|=\sqrt{v_x^2+v_y^2}$

### Normalized vectors
## References

---
Planted: 2025-07-05
Last tended: 2025-07-05