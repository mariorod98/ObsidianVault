# 🔴 Count the number of different countries that a map contains.

## Description
A rectangular map consisting of N rows and M columns of square areas is given. Each area is painted with a certain color.

Two areas on the map _belong to the same country_ if the following conditions are met:

-   they have the same color;
-   it is possible to travel from one area to the other orthogonally (that is, by moving only north, south, west or east) without moving over areas of a different color.

The map can be described by a zero-indexed matrix A consisting of N rows and M columns of integers. The color of each area is described by the corresponding element of the matrix. Two areas have the same color if and only if their corresponding matrix elements have the same value.

For example, consider the following matrix A consisting of seven rows and three columns:

```
A[0][0] = 5    A[0][1] = 4    A[0][2] = 4
A[1][0] = 4    A[1][1] = 3    A[1][2] = 4
A[2][0] = 3    A[2][1] = 2    A[2][2] = 4
A[3][0] = 2    A[3][1] = 2    A[3][2] = 2
A[4][0] = 3    A[4][1] = 3    A[4][2] = 4
A[5][0] = 1    A[5][1] = 4    A[5][2] = 4
A[6][0] = 4    A[6][1] = 1    A[6][2] = 1
```

Matrix A describes a map that is colored with five colors.

Write a function

```cpp
int solution(vector< vector<int> > &A);
```


that, given a zero-indexed matrix A consisting of N rows and M columns of integers, returns the number of different countries to which the areas of the map described by matrix A belong.

For example, given matrix A consisting of seven rows and three columns corresponding to the example above, the function should return 11.

Write an ****efficient**** algorithm for the following assumptions:

-   N and M are integers within the range [1..300,000];
-   the number of elements in matrix A is within the range [1..300,000];
-   each element of matrix A is an integer within the range [−1,000,000,000..1,000,000,000].

## Solution (wrong)

```cpp
void paint_map(vector< vector<int> >& A,
  vector< vector<int> >& map,
  int& countries,
  int row,
  int col) {

  int value = A[row][col];
  int top_row = row - 1;
  int bottom_row = row + 1;
  int left_col = col - 1;
  int right_col = col + 1;

  printf("\n\nChecking cell [%i,%i]\n", row, col);

  if (top_row >= 0 &&
    map[top_row][col] != 0 &&
    A[top_row][col] == value) {
    map[row][col] = map[top_row][col];
    printf("It is the same country as cell [%i,%i]\n", top_row, col);

  }
  else if (right_col < A[0].size() &&
    map[row][right_col] != 0 &&
    A[row][right_col] == value) {
    map[row][col] = map[row][right_col];
    printf("It is the same country as cell [%i,%i]\n", row, right_col);

  }
  else if (bottom_row < A.size() &&
    map[bottom_row][col] != 0 &&
    A[bottom_row][col] == value) {
    map[row][col] = map[bottom_row][col];
    printf("It is the same country as cell [%i,%i]\n", bottom_row, col);
  }
  else if (left_col >= 0 &&
    map[row][left_col] != 0 &&
    A[row][left_col] == value) {
    map[row][col] = map[row][left_col];
    printf("It is the same country as cell [%i,%i]\n", row, left_col);
  }
  else {
    map[row][col] = ++countries;
    printf("It is a new country. Countries: %i\n", countries);
  }


  if (top_row >= 0 && map[top_row][col] == 0) {
    paint_map(A, map, countries, top_row, col);
  }
  if (right_col < A[0].size() && map[row][right_col] == 0) {
    paint_map(A, map, countries, row, right_col);
  }
  if (bottom_row < A.size() && map[bottom_row][col] == 0) {
    paint_map(A, map, countries, bottom_row, col);
  }
  if (left_col >= 0 && map[row][left_col] == 0) {
    paint_map(A, map, countries, row, left_col);
  }
}

int solution(vector< vector<int> >& A) {
  vector<vector<int>> map(A.size(), std::vector<int>(A[0].size(), 0));
  int countries = 0;

  paint_map(A, map, countries, 0, 0);
  return countries;
}
```


## Solution ChatGPT O(MN)
```cpp
void dfs(vector< vector<int> > &A, vector< vector<bool> > &visited, int i, int j) {
    int color = A[i][j];
    visited[i][j] = true;
    
    // check neighboring cells
    if (i > 0 && !visited[i-1][j] && A[i-1][j] == color) {
        dfs(A, visited, i-1, j);
    }
    if (i < A.size()-1 && !visited[i+1][j] && A[i+1][j] == color) {
        dfs(A, visited, i+1, j);
    }
    if (j > 0 && !visited[i][j-1] && A[i][j-1] == color) {
        dfs(A, visited, i, j-1);
    }
    if (j < A[0].size()-1 && !visited[i][j+1] && A[i][j+1] == color) {
        dfs(A, visited, i, j+1);
    }
}

int solution(vector< vector<int> > &A) {
    int N = A.size();
    int M = A[0].size();
    
    vector< vector<bool> > visited(N, vector<bool>(M, false));
    int num_countries = 0;
    
    // perform DFS traversal on unvisited nodes
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < M; j++) {
            if (!visited[i][j]) {
                dfs(A, visited, i, j);
                num_countries++;
            }
        }
    }
    
    return num_countries;
}
```