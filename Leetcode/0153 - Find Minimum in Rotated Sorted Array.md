---
date: 2025-03-22
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- There can be -5000 in input array
- my thinking
- we can do a [[Binary Search]], and select the immediate left ~~and right~~ value, and compare if the left one is greater than current 

> [!info] References
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0, mid = 0, right = nums.length - 1;

        while (left < right) {
            mid = left + (right - left) / 2;

            if (nums[mid] > nums[right])
                left = mid + 1;
            else
                right = mid;
        }
        return nums[left];
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 