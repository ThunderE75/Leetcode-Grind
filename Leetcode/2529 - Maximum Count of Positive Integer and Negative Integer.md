---
Date: 2025-03-12
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- input **nums** can be either increasing or dupes.
- we can easily solve in $O(n)$ time, but for $O(log~n)$,we can maybe just count all *-ve* then count zeros & subtract them with length.
- or we can do binary search thing half divide until we find zero ?, but we will need to actually count them
- 

> [!info] References
> - 
### Optimized Solution
```java fold title="Binary Serach Method"
class Solution {
    public int maximumCount(int[] nums) {
        int n = nums.length;
        // finds the first non-negative (0) number -> i.e count of negative numbers
        int nege = binarySearch(nums, 0);
        // finds the first positive number -> i.e count of positive numbers
        int posi = n - binarySearch(nums, 1);
        return Math.max(nege, posi);
    }

    public int binarySearch(int[] nums, int target) {
        int left = 0;
        int right = nums.length-1;
        int res = nums.length;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target)
                left = mid + 1;
            else {
                res = mid;
                right = mid - 1;
            }
        }
        return res;
    }
}

```
### Follow Up Solution
```java

```
### Initial Solution
```java title="Naive Solution"
class Solution {
    public int maximumCount(int[] nums) {
        int n = nums.length;
        int count = 0;
        int zeros = 0;
        int i = 0;
        
        while (i < n && nums[i] < 0) {
            count++;
            i++;
        }
        
        while (i < n && nums[i] == 0) {
            zeros++;
            i++;
        }
        
        return Math.max(count, (n - zeros - count));
    }
}

```
### Key Takeaways
- Ways to solve
	- Naive count -vw & zeros, return max
	- [[0704 - Binary Search]] Baby!!!
	- 

*similar to:* 
- [[0704 - Binary Search]]
- 