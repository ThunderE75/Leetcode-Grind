---
Hardness: Easy
No.: "3105"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/description/
Date: 2025-02-03T19:08
Next Review: February 7, 2025
---
## Useful Video Resources

## Initial Solution

> [!info] Longest Strictly Increasing or Strictly Decreasing Subarray - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/solutions/6365025/simple-and-easy-solution-beats-100-c-java-python-javascript/?envType=daily-question&envId=2025-02-03](https://leetcode.com/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/solutions/6365025/simple-and-easy-solution-beats-100-c-java-python-javascript/?envType=daily-question&envId=2025-02-03)  

```Java
class Solution {
    public int longestMonotonicSubarray(int[] nums) {
        int inc = 1; // To store the length of the increasing subarray
        int dec = 1; // To store the length of the decreasing subarray
        int n = nums.length;
        int maxLen = 1;
		
        for (int i = 1; i < n; i++) {
            if (nums[i - 1] < nums[i]) { // When there is a increasing subarray
                inc++;
                dec = 1;
            } else if (nums[i - 1] > nums[i]) { // When there is a decreasing subarray
                dec++;
                inc = 1;
            } else { // when both are same
                inc = 1;
                dec = 1;
            }
            maxLen = Math.max(maxLen, Math.max(inc, dec));
        }
        return maxLen;
    }
}
```

## Key Takeaways