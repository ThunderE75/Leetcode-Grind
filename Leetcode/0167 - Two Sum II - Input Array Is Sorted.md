---
Hardness: Medium
No.: "167"
Solution Type:
  - 2 Pointer
URL: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/
Date: 2025-01-08T01:45
Hint: Simple 2 Pointer
---

## Useful Video Resources
- [TWO SUM II - Amazon Coding Interview Question - Leetcode 167 - Python - YouTube](https://youtu.be/cQ1Oz4ckceM)
## Initial Solution

```Java fold
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int start = 0, end = numbers.length - 1;
        while (start < end) {
            if (numbers[start] + numbers[end] > target)
                --end;
            else if (numbers[start] + numbers[end] < target)
                ++start;
            else
                break;
        }
        return new int[] { start + 1, end + 1 };
    }
}
```

## Key Takeaways
- Simple 2 pointers ([[Sliding Window]]) approach
    - if the sum is greater than target
        - move right pointer
    - otherwise
        - move left pointer
    - return when it reaches the target
*similar to:* 
- [[0001 - Two Sum]]
- [[0015 - 3Sum]]
- 