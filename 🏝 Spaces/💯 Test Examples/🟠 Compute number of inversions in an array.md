
# 🟠 Compute number of inversions in an array



## Description

An array A consisting of N integers is given. An _inversion_ is a pair of indexes (P, Q) such that P < Q and A[Q] < A[P].
Write a function:
```cpp
int solution(vector<int> &A);
```

that computes the number of inversions in A, or returns −1 if it exceeds 1,000,000,000.
For example, in the following array:

A[0] = -1 A[1] = 6 A[2] = 3 A[3] = 4 A[4] = 7 A[5] = 4

there are four inversions:

(1,2) (1,3) (1,5) (4,5)

so the function should return 4.

Write an ***efficient*** algorithm for the following assumptions:

-   N is an integer within the range [0..100,000];
-   each element of array A is an integer within the range [−2,147,483,648..2,147,483,647].

## Solution O(n\*log(n))

```cpp
int merge(vector<int> &A, vector<int> &temp, int left, int mid, int right) {
    // initialize pointers and count variable
    int i = left, j = mid + 1, k = left;
    int count = 0;
    
    // merge two halves and count the number of inversions
    while (i <= mid && j <= right) {
        if (A[i] <= A[j]) {
            temp[k++] = A[i++];
        } else {
            temp[k++] = A[j++];
            count += mid - i + 1; // increment count by the number of remaining elements in the left half
        }
    }
    
    // copy remaining elements to temp array
    while (i <= mid) temp[k++] = A[i++];
    while (j <= right) temp[k++] = A[j++];
    
    // copy sorted elements back to original array
    for (i = left; i <= right; i++) A[i] = temp[i];
    
    // return the number of inversions
    return count;
}

int mergeSort(vector<int> &A, vector<int> &temp, int left, int right) {
    if (left >= right) return 0; // base case: single element
    int mid = left + (right - left) / 2; // find the middle index
    int count = mergeSort(A, temp, left, mid); // recursively sort the left half
    count += mergeSort(A, temp, mid + 1, right); // recursively sort the right half
    count += merge(A, temp, left, mid, right); // merge the two halves and count the number of inversions
    if (count > 1000000000) return -1; // check if the number of inversions exceeds the limit
    return count;
}

int solution(vector<int> &A) {
    int n = A.size();
    vector<int> temp(n); // temporary array for merging
    return mergeSort(A, temp, 0, n - 1); // call merge sort function
}
```