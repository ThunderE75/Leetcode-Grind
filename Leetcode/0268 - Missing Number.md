---
Date: 2025-04-05
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/missing-number/description/
Hint: 
Clarity: Crystal
Solution Type:
  - ⚙️ Bit Manipulation
  - 🧠 Design
Hardness: Easy
cssclasses:
  - programming-notes
  - no_url_underline
---

## Intuition
- Ways to solve this 
	- Sort, then traverse to find missing 
	- Expected Sum `{java}n(n+1)/2` - actual sum
	- or, XOR each value & index + 1
## Solution
```java title="Initial Attempt"
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        long check = n*(n + 1) / 2;
        long sum = 0;
        for (int i : nums)
            sum += (int) i;

        return (int) check - sum;
    }
}
```

```java fold title="XOR Index & Values"
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int curr = 0;
        int sum = 0;
        for (int i = 0; i<n; i++){
            curr = nums[i] ^ i+1;
            sum ^=curr;
        }

        return sum;
    }
}
```
## Key Takeaways
- 

> [!info] References
> 1. [Missing Number - LeetCode](https://leetcode.com/problems/missing-number/submissions/1597625938)

*similar to:* 
- 