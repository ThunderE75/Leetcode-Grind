---
Hardness: Easy
No.: "100"
Solution Type:
  - DFS
Que Type:
  - Binary Tree
Clarity: Medium
URL: https://leetcode.com/problems/same-tree/description/
Date: 2024-12-17T17:00
Week:
  - Week 4
Next Review: December 21, 2024
---
## Intuition
- What the fuck, this is simple but i can't come up with the code
- Okay, cases
	- When both nodes are null
	- When both node have the the same value (& are !null)
	- traverse via recursion on both left and right nodes
## Solution
```java title="Initial Attempt"
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null && q == null ) return true;
        if(p != null && q != null  && p.val == q.val)
            return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
        return false;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [LeetCode 100: The Same Tree - Interview Prep Ep 21](https://youtu.be/2Pe6e0KbgFI)

*similar to:* 
- 