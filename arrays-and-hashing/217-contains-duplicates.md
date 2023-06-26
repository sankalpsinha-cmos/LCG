# Contains Duplicates
### Problem Statement
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

Example 1:
Input: nums = [1,2,3,1]
Output: true

Example 2:
Input: nums = [1,2,3,4]
Output: false

Example 3:
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

---

### Naive Solution
Logic:
Two for loops, outer loop tracks the target int and the inner loop walks through the list to see if we have another target int.

TC: O(N^2) SC: O(1) TLE
```python
def containsDuplicate(self, nums: List[int]) -> bool:
    for i in range(len(nums)):
        for j in range(i+1, len(nums)):
            if nums[i] == num[j]:
                return True
    return False
```

### Sub-optimal solution
Logic: Sort the list and then walk through the sorted list to see if any two adjacent integers are the same, if yes then we have a duplicate else no duplicate.

TC: O(NlogN) SC: O(N) Pass
```python
def containsDuplicate(self, nums: List[int]) -> bool:
    nums.sort()
    for i in range(1, len(nums)):
        if nums[i-1] == nums[i]:
            return True
    return False
```

### Optimal solution
Logic: Make a hash set in python see if the length of the hash set is the same as that of the original list. If yes, then no duplicates else there are duplicates.

TC: O(N) SC: O(N) Pass

```python
def containsDuplicate(self, nums: List[int]) -> bool:
    return not len(nums) == len(set(nums))
```