# Container with most water
## Problem Statement
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

[problem image](https://images.app.goo.gl/xPRDRVfskhpSj9uW6)

---

## Naive Solution
Logic: Two loops, the outer loop keeps track of the left end of the container
and the inner loop extends the right end of the container, inside the two loops we calculate the volume of water contained and keep track of the largest volume of water.

TC: O(N^2) SC: O(1) TLE
```python
def maxArea(self, height: List[int]) -> int:
    most_water = 0
    for i in range(len(height)):
        for j in range(i+1, len(height)):
            if most_water < (j-i) * min(height[i], height[j]):
                most_water = (j-i) * min(height[i], height[j])
    return most_water
```

## Optimal Solution
Logic: Two pointer approach, consider the whole list as the largest bucket you can make not necessarily containing the most water. We now calculate the volume of water and keep track of the largest volume of water. Now, we move the left or right end of the bucket based on which end is less tall and move inwards till left == right.

TC: O(N) SC: O(1), Pass
```python
def maxArea(self, height: List[int]) -> int:
    left, right, most_water = 0, len(height) - 1, 0
    
    while left < right:
        if (right-left) * min(height[left], height[right]) > most_water:
            most_water = (right-left) * min(height[left], height[right])
        if height[left] < height[right]:
            left += 1
        elif height[left] > height[right]:
            right -= 1
        else:
            left += 1
            right -= 1
    return most_water
```
