# Calculate the number of slices in which (maximum - minimum <= K).
## Definition

An integer K and a non-empty array A consisting of N integers are given.

A pair of integers (P, Q), such that 0 ≤ P ≤ Q < N, is called a _slice_ of array A.

A _bounded slice_ is a slice in which the difference between the maximum and minimum values in the slice is less than or equal to K. More precisely it is a slice, such that max(A[P], A[P + 1], ..., A[Q]) − min(A[P], A[P + 1], ..., A[Q]) ≤ K.

The goal is to calculate the number of bounded slices.

For example, consider K = 2 and array A such that:

A[0] = 3 A[1] = 5 A[2] = 7 A[3] = 6 A[4] = 3

There are exactly nine bounded slices: (0, 0), (0, 1), (1, 1), (1, 2), (1, 3), (2, 2), (2, 3), (3, 3), (4, 4).

Write a function:

```cpp
int solution(int K, vector<int> &A);
```


that, given an integer K and a non-empty array A of N integers, returns the number of bounded slices of array A.

If the number of bounded slices is greater than 1,000,000,000, the function should return 1,000,000,000.

For example, given:

A[0] = 3 A[1] = 5 A[2] = 7 A[3] = 6 A[4] = 3

the function should return 9, as explained above.

Write an ****efficient**** algorithm for the following assumptions:

-   N is an integer within the range [1..100,000];
-   K is an integer within the range [0..1,000,000,000];
-   each element of array A is an integer within the range [−1,000,000,000..1,000,000,000].

## Solution

```cpp
int solution(int K, vector<int> &A) {
    unsigned int bounds = 0;
    for(unsigned int i = 0; i < A.size(); i++) {
        unsigned int min = i;
        unsigned int max = i;
        bounds++;

        for(unsigned int j = i + 1; j < A.size(); j++) {
            if(A[j] < A[min]) min = j;
            if(A[j] > A[max]) max = j;
            if(A[max] - A[min] > K) break;
            bounds++;

            if(bounds > 1000000000) return 1000000000;
        }
    }

    return bounds;
}
```