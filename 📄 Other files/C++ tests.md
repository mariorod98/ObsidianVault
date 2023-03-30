up::
tags:: #state/seedling

# C++ tests

## Merge Intervals
Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.


```cpp
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        // create copy because we don't want to modify original vector     
        vector<vector<int>> intervals_sorted = intervals;
        // sort the intervals
        sort(intervals_sorted.begin(), intervals_sorted.end());

        // create solution
        vector<vector<int>> solution;

        // for each interval
        for(int i = 0; i < intervals_sorted.size(); i++) {
            vector<int>& next = intervals_sorted[i];
            // iffirst interval or if the intervals do not overlap
            if(solution.empty() || solution.back()[1] < next[0]) {
                solution.push_back(next);
            } // if new upper bound is greater than the current upper bound
            else if(solution.back()[1] < next[1]){
                solution.back()[1] = next[1];
            }
        }

        return solution;
    }
```

## References

---
Planted: 2023-03-16
Last tended: 2023-03-16