---
Hardness: Easy
No.: "704"
Solution Type:
  - Recursion
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/binary-search/description/
Date: 2024-11-05T03:01
Week:
  - Week 1
Session 1: Mid
Next Review: November 15, 2024
Remarks: Try using Recursion, check mid, then check if both left & right bounds are correct, the check rest
SR Notes:
  - "[[1-704]]"
---

## Solution
```Java title="Iterative Approach"
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length-1;
        while(left <= right){
            int mid = left + (right-left)/2;
            if (nums[mid] == target) return mid;
            else if (target < nums[mid])
                right = mid-1;
            else if (target > nums[mid])
                left = mid+1;
        }
        return -1;
    }
}
```

```java fold title="Recursive Approach"
class Solution {
    public int search(int[] nums, int target) {
        return binarySearch(nums, 0, nums.length-1, target);
    }
    public static int binarySearch(int[] nums, int left, int right, int target) {
        int mid = left + (right-left)/2;

        // if found
        if (nums[mid] == target) return mid;

        // if not found
        if (left >= right) return -1;

        if (target < nums[mid])
            return binarySearch(nums, left, mid-1, target);

        return binarySearch(nums, mid+1, right, target);
    }
}
```
## Key Takeaways
- Mid is calculated this way to prevent integer overflow. `{java} int mid = left + (right-left)/2;` 

> [!info] References
> 1. [Binary Search Algorithm in 100 Seconds - YouTube](https://youtu.be/MFhxShGxHWc)
> 2. [Learn Binary Search in 10 minutes 🪓 - YouTube](https://www.youtube.com/watch?v=xrMppTpoqdw&list=PLZPZq0r_RZON1eaqfafTnEexRzuHbfZX8&index=10&t=127s&pp=iAQB) 
> 3. [Extra, Extra - Read All About It: Nearly All Binary Searches and Mergesorts are](https://blog.research.google/2006/06/extra-extra-read-all-about-it-nearly.html)
>

*similar to:* 
- 