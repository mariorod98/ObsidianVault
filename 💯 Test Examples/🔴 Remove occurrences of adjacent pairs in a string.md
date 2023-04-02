# 🔴 Remove occurrences of adjacent pairs in a string

## Description
A string S containing only the letters "A", "B" and "C" is given. The string can be transformed by removing one occurrence of "AA", "BB" or "CC".

Transformation of the string is the process of removing letters from it, based on the rules described above. As long as at least one rule can be applied, the process should be repeated. If more than one rule can be used, any one of them could be chosen.

Write a function:
```cpp
string solution(string &S);
```


that, given a string S consisting of N characters, returns any string that can result from a sequence of transformations as described above.

For example, given string S = "ACCAABBC" the function may return "AC", because one of the possible sequences of transformations is as follows:

```
A(CC)AABBC
(AA)ABBC
A(BB)C
AC
```

Also, given string S = "ABCBBCBA" the function may return "", because one possible sequence of transformations is:

```
ABC(BB)CBA
AB(CC)BA
A(BB)A
(AA)

```

Finally, for string S = "BABABA" the function must return "BABABA", because no rules can be applied to string S.

Write an ****efficient**** algorithm for the following assumptions:

-   the length of string S is within the range [0..50,000];
-   string S is made only of the following characters: 'A', 'B' and/or 'C'.

## Solution O(N\*\*2)

```cpp
// calculate the compressed string in the substring [ini,end)
string divide_and_conquer(string& S, int ini, int end) {
  string solution = "";
  if (end - ini <= 1) {
    return solution + S[ini];
  }
  if (end - ini == 2) {
    if (S[ini] == S[end - 1]) {
      return solution;
    }
    else {
      solution = solution + S[ini];
      return solution + S[end - 1];
    }
  }

  unsigned int mid = (ini + end) / 2;

  string left = divide_and_conquer(S, ini, mid);
  string right = divide_and_conquer(S, mid, end);

  int left_pos = left.size() - 1;
  int right_pos = 0;

  if (left_pos < 0 || right_pos >= right.size()) {
    return left + right;
  }

  while (left_pos >= 0 || right_pos < right.size()) {
    if (left[left_pos] == right[right_pos]) {
      left_pos--;
      right_pos++;
    }
    else break;
  }

  string left_substr = "";
  for (int i = 0; i <= left_pos; i++) {
    solution = solution + left[i];
  }

  string right_substr = "";
  for (int i = right_pos; i < right.size(); i++) {
    solution = solution + right[i];
  }

  return solution;
}

string solution(string& S) {
  return divide_and_conquer(S, 0, S.size());
}
```

## Solution by ChatGPT using a stack O(N)