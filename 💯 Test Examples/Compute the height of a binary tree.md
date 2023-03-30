# Compute the height of a binary tree

## Description

In this problem we consider binary trees, represented by pointer data structures.

A _binary tree_ is either an empty tree or a node (called the _root_) consisting of a single integer value and two further binary trees, called the _left subtree_ and the _right subtree_.

A _path_ in a binary tree is a non-empty sequence of nodes that one can traverse by following the pointers. The _length_ of a path is the number of pointers it traverses. More formally, a path of length K is a sequence of nodes P[0], P[1], ..., P[K], such that node P[I + 1] is the root of the left or right subtree of P[I], for 0 ≤ I < K. For example, the sequence of nodes with values 5, 3, 21 is a path of length 2 in the tree from the above figure. The sequence of nodes with values 10, 1 is a path of length 1. The sequence of nodes with values 21, 3, 20 is not a valid path.

The _height_ of a binary tree is defined as the length of the longest possible path in the tree. In particular, a tree consisting of only one node has height 0 and, conventionally, an empty tree has height −1. For example, the tree shown in the above figure is of height 2.

### Problem

Write a function:
```cpp
int solution(tree * T);
```


that, given a non-empty binary tree T consisting of N nodes, returns its height. For example, given tree T shown in the figure above, the function should return 2, as explained above. Note that the values contained in the nodes are not relevant in this task.

### Technical details

A binary tree can be given using a pointer data structure. Assume that the following declarations are given:

```cpp
struct tree { 
	int x; 
	tree * l; 
	tree * r; 
};
```

An empty tree is represented by an empty pointer (denoted by NULL). A non-empty tree is represented by a pointer to an object representing its root. The attribute x holds the integer contained in the root, whereas attributes l and r hold the left and right subtrees of the binary tree, respectively.

### Assumptions

Write an ***efficient*** algorithm for the following assumptions:

-   N is an integer within the range [1..1,000];
-   the height of tree T (number of edges on the longest path from root to leaf) is within the range [0..500].

## Solution

```cpp
// Recursive function called for every node to calculate
// its height
int expand_node(tree* T, int current_height) {
    // If the node does not exist, return the previous height
    if(T == nullptr) return current_height;

    // if the node exists, calculate the current height
    current_height += 1;

    // calculate the height of the left and right branch
    int l_height = expand_node(T->l, current_height);
    int r_height = expand_node(T->r, current_height);

    // return height of the highest branch
    return l_height > r_height ? l_height : r_height;
}

int solution(tree * T) {
    return expand_node(T, -1);
}
```