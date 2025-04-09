---
date: 2025-04-04
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/find-the-duplicate-number/description/
Hint: 
Clarity: Medium
Solution Type:
  - 2 Pointer
Hardness:
  - Medium
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- The basic naive solution is a [[Hash Set]]
- if the elements in the array are between `1 & n` and the constraints `All the integers in nums appear only once` suggest a mathematical solution, that we add every number between 1 & n and subtract it by the sum of the array, but example 3 makes that assumption invalid i.e. `except for precisely one integer which appears two or more times.` 
- WHAT THE FUCK !?
- After watching Ref-1, it's a [[Floyd’s Cycle-Finding Algorithm]] technique. See similar questions 
- 
## Solution
```java title="Naive Initial Attempt"
class Solution {
    public int findDuplicate(int[] nums) {
        int res = -1;
        HashSet<Integer> set = new HashSet<>();
        for (int i : nums)
            if (!set.contains(i))
                set.add(i);
            else
                res = i;
        return res;
    }
}
```

```java fold title="Floyd's Cycle"
class Solution {
    public int findDuplicate(int[] nums) {
        int p1 = nums[0]; // slow
        int p2 = nums[nums[0]]; // fast

        // untill we find a cycle 
        while (p1 != p2) {
            p1 = nums[p1];
            p2 = nums[nums[p2]];
        }
        // resitiing  p2 at start
        p2 = 0;
        while (p1 != p2) {
            p1 = nums[p1];
            p2 = nums[p2];
        }
        return p2;
    }
}
```
## Key Takeaways
- 

> [!info] References
> 1. [Find the Duplicate Number - Floyd's Cycle Detection - Leetcode 287 - Python](https://youtu.be/wjYnzkAhcNk) 

*similar to:* 
- [[0141 - Linked List Cycle]]
- [[0142 - Linked List Cycle II]] 
- 