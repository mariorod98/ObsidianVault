# 🔴 Remove occurrences of adjacent pairs in a string

## Description

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