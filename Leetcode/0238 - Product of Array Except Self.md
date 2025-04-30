---
Date: 2025-02-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/product-of-array-except-self/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: Medium
cssclasses:
  - programming-notes
  - no-properties
---

### Intuition
- Need to use prefix & postfix sums
- Follow up, try not to use different arrays to store the prefix and postfix 

> [!info] References
> - [Product of Array Except Self - Leetcode 238 - Python - YouTube](https://youtu.be/bNvIQI2wAjk)
> - [LeetCode 238. Product of Array Except Self (Solution Explained) - YouTube](https://youtu.be/tSRFtR3pv74)
### Optimized Solution
```java fold title="Storing the prefix & postfix in result arrray itself"
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int temp = 1;
        int[] res = new int[n];

        // Storing the prefix sum in theresult array
        res[0] = 1;
        for (int i = 1; i < n; i++) 
            res[i] = nums[i-1] * res[i-1];

        for (int i = n - 1; i >= 0; i--){
            res[i] *= temp;
            temp *= nums[i];
        }

        return res;
    }
}
```

### Initial Solution
```java title="Using seprate Prefix & Postfix Arrays"
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int total= 0;
        int[] pre = new int[n];
        int[] post = new int[n];
        int[] res = new int[n];
        pre[0] = nums[0];
        post[n-1] = nums[n-1];
        
        for (int i=1; i < n; i++)
            pre[i] = pre[i-1] * nums[i];
        for (int i=n-2; i >= 0; i--)
            post[i] = post[i+1] * nums[i];
        
        res[0] = post[1];
        res[n-1] = pre[n-2];
        for (int i=1; i < n-1; i++)
            res[i] = pre[i-1] * post[i+1];
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 