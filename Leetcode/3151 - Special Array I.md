---
Hardness: Easy
No.: "3151"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/special-array-i/description/
Date: 2025-02-01T15:44
Next Review: February 5, 2025
---
> [!info] Special Array I - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/special-array-i/solutions/6356285/simple-java-solution-module-bit-manipula-cdj2/](https://leetcode.com/problems/special-array-i/solutions/6356285/simple-java-solution-module-bit-manipula-cdj2/)  

## Useful Video Resources

## Initial Solution

```Java
class Solution {
    public boolean isArraySpecial(int[] nums) {
        for (int i = 0; i < nums.length - 1; i++) {
            int a = nums[i] & 1;
            int b = nums[i + 1] & 1;
            if (a == b)
                return false;
        }
        return true;
    }
}
```