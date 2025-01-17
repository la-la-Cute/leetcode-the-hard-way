---
description: 'Author: @wingkwong'
---

# Backtracking

A backtracking algorithm is used to construct a solution recursively by starting with an empty solution and adding solution one by one. Let's take [0046 - Permutations (Medium)](../../solutions/0000-0099/0046-permutations-medium.md) as an example, if we have an array `nums` of distinct integers, what are all the possible permutations? If the input is `[1,2,3]`, then the permutations would be `[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]`. In C++, it is easy to solve this problem by using the built-in STL `next_permutation`. However, we can also solve it using backtracking.

The general steps are as follows.

1. Sort the input array if necessary. However, in this example, sorting is not necessary.

```cpp
sort(nums.begin(), nums.end());
```

2\. Define `ans` and `tmp` where `ans` is the array storing all final permutations and `tmp` is used to store possible permutations at some point.

```cpp
vector<vector<int>> ans;
vector<int> tmp;
```

3\. Call `backtrack()` function in main

```cpp
backtrack(nums, ans, tmp);
```

4\. Let's add logic in `backtrack()` function. First we need to define the exit criteria. When should we push `tmp` to `ans`? If `tmp` already got enough candidates, then we can push `tmp` to `ans`.

```cpp
if ((int) tmp.size() == (int) nums.size()) {
    ans.push_back(tmp);
    return;
}
```

5\. Iterate each number, check If the candidate has been used or not, skip it if it is already in `tmp`. Otherwise, push it to `tmp` and call `backtrack()` again. After that, remove the previous candidate from `tmp` and move to the next candidate.

```cpp
for (auto x : nums) {
    if (find(tmp.begin(), tmp.end(), x) != tmp.end()) continue;
    tmp.push_back(x);
    backtrack(nums, ans, tmp);
    tmp.pop_back();   
}
```

### Suggested Problems:

* [0039 - Combination Sum (Medium)](../../solutions/0000-0099/0039-combination-sum-medium.md)
* [0040 - Combination Sum II (Medium)](../../solutions/0000-0099/0040-combination-sum-ii-medium.md)
* [0046 - Permutations (Medium)](../../solutions/0000-0099/0046-permutations-medium.md)
* [0078 - Subsets (Medium)](../../solutions/0000-0099/0078-subsets-medium.md)
