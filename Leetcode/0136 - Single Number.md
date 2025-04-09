---
date: 2025-04-05
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/single-number/description/
Hint: XOR same number will give 0
Clarity: Crystal
Solution Type: 
Hardness:
  - Easy
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- Dead simple, XOR same number will give 0 
- so `{java}5 ^ 5 == 0` 
## Solution
```java title="Initial Attempt"
class Solution {
    public int singleNumber(int[] nums) {
        int sum = 0;
        for(int i : nums)
            sum ^=i;
        return sum;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. 

*similar to:* 
- 