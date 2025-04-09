---
Hardness: Medium
No.: "53"
Solution Type:
  - Dynamic Programing
Que Type:
  - Array
Clarity: High
URL: https://leetcode.com/problems/maximum-subarray/description/
Date: 2025-01-03T12:31
Week:
  - Week 4
Next Review: January 7, 2025
---
## Useful Video Resources

- [Maximum Subarray - Amazon Coding Interview Question - Leetcode 53 - Python - YouTube](https://youtu.be/5WZl3MMT0Eg)

## Solution

## Key Takeaways

```Java
class Solution {
    public int maxSubArray(int[] nums) {
        int sum = 0;
        int max = Integer.MIN_VALUE;
        // i = end
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            max = Math.max(max, sum);
            if (sum < 0) // i.e, -ve
                sum = 0;
        }
        return max;
    }
}
```

- Use [[Kadane's Algorithm]]