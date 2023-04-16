
# 🟠 Given a tree, find a downward path with the maximal number of direction changes.

## Description

In this problem we consider binary trees. Let's define a _turn_ on a path as a change in the direction of the path (i.e. a switch from right to left or vice versa). A _zigzag_ is simply a sequence of turns (it can start with either right or left). The length of a zigzag is equal to the number of turns.


### Problem

Write a function:

```cpp
int solution(tree * T);
```

that, given a non-empty binary tree T consisting of N nodes, returns the length of the longest zigzag starting at the root.

For example, given tree T shown in the figure above, the function should return 2, as explained above. Note that the values contained in the nodes are not relevant in this task.

### Technical details

A binary tree can be specified using a pointer data structure. Assume that the following declarations are given:

```cpp
struct tree { 
	int x; 
	tree * l; 
	tree * r; 
};
```

An empty tree is represented by an empty pointer (denoted by NULL). A non-empty tree is represented by a pointer to an object representing its root. The attribute x holds the integer contained in the root, whereas attributes l and r hold the left and right subtrees of the binary tree, respectively.

For the purpose of entering your own test cases, you can denote a tree recursively in the following way. An empty binary tree is denoted by None. A non-empty tree is denoted as (X, L, R), where X is the value contained in the root and L and R denote the left and right subtrees, respectively. The tree from the above figure can be denoted as:

(5, (3, (20, (6, None, None), None), None), (10, (1, None, None), (15, (30, None, (9, None, None)), (8, None, None))))

### Assumptions

Write an ****efficient**** algorithm for the following assumptions:

-   N is an integer within the range [1..100,000];
-   the height of tree T (number of edges on the longest path from root to leaf) is within the range [0..800].

## Solution O(n)

```cpp
int turn_left(tree* T, int zigzag_count, bool was_left);

int turn_right(tree* T, int zigzag_count, bool was_left) {
    if(T == nullptr) return zigzag_count;

    if(was_left == true) {
        zigzag_count += 1;
    }

    int right = turn_right(T->r, zigzag_count, false);
    int left = turn_left(T->l, zigzag_count, false);

    return right > left ? right : left;
}

int turn_left(tree* T, int zigzag_count, bool was_left) {
    if(T == nullptr) return zigzag_count;

    if(was_left == false) {
        zigzag_count += 1;
    }

    int left = turn_left(T->l, zigzag_count, true);
    int right = turn_right(T->r, zigzag_count, true);

    return right > left ? right : left;
}

int solution(tree * T) {
    int left = turn_left(T->l, 0, true);
    int right = turn_right(T->r, 0, false);
  
    return right > left ? right : left;
}
```

## Solution ChatGPT O(N)

```cpp
int solution(tree * T) {
    if (T == NULL) {
        return 0;
    } else {
        return max(zigzag(T->l, true, 1), zigzag(T->r, false, 1));
    }
}

int zigzag(tree * T, bool is_left, int length) {
    if (T == NULL) {
        return length;
    } else {
        if (is_left) {
            return max(
			            zigzag(T->r, false, length + 1), 
						zigzag(T->l, true, 1)
					);
        } else {
		    return max(
					    zigzag(T->l, true, length + 1), 
					    zigzag(T->r, false, 1)
					);
        }
    }
}

```