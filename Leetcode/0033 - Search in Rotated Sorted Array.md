---
Date: 2025-03-24
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/search-in-rotated-sorted-array/description/
Hint: 
Clarity: Low
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- Binary Search
- Working
	- **Kink** is the start of the array before rotation
	- Find `mid`
	- if `{java}target < mid` & the **kink** is on the right.
		- Then we need to decided which side we want to search
		- So, we compare the target with the `left` pointer, if `{java}target < left` then we will search on the right of the mid, because the number cant be on the left side.
---
- if `{java}mid <= left` we know we are on the left sorted portion

> [!info] References
> - [Search in rotated sorted array - Leetcode 33 - Python - YouTube](https://youtu.be/U8XENwh8Oy8)
### Optimized Solution
```java

```
### Follow Up Solution
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, mid = 0, right = nums.length - 1;
        while (left <= right) {
            mid = left + (right - left) / 2;
            if (target == nums[mid])
                return mid;

            // we are on the right portion of the rotated array
            else if (nums[mid] >= nums[left]) {
                if (nums[left] <= target && target <= nums[mid])
                    right = mid - 1;
                else
                    left = mid + 1;
            
            // we are on the left portion of the rotated array
            } else {
                if (nums[mid] <= target && target <= nums[right])
                    left = mid + 1;
                else
                    right = mid - 1;
            }
        }
        return -1;
    }
}
```
### Initial Solution
```java

```
### Key Takeaways
- 

*similar to:* 
- 