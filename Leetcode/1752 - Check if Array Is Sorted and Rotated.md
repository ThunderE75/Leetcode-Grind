---
Hardness: Easy
No.: "1752"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/
Date: 2025-02-02T23:43
Next Review: February 6, 2025
---
## Useful Video Resources

## Solution

```Java
class Solution {
    public boolean check(int[] nums) {
        int n = nums.length;
        int anomaly = 0;
        for (int i = 0; i < n; i++) {
            if (nums[i] > nums[(i + 1) % n])
                anomaly++;
            if (anomaly > 1)
                return false;
        }
        return true;
    }
}
```

## Key Takeaways