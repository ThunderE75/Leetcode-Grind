---
Date: 2024-11-05
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/invert-binary-tree/description/
Hint: Recursion; until root is null, DFS; swap;
Clarity: Medium
Solution Type:
  - DFS
Hardness: Easy
cssclasses:
  - programming-notes
  - no_url_underline
---

## Intuition
- Okay, we need to swap left and right
- Should be pretty easy using DFS & Recursion
- Iterative approach is weird & requires a stack or a list
## Solution
```java title="Initial Attempt"
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) return root;
        
        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);

        root.left = right;
        root.right = left;
        return root;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Neetcode - Invert Binary Tree - Depth First Search - Leetcode 226](https://youtu.be/OnSn2XEQ4MY)
> 2. [Nick White - LeetCode Invert Binary Tree Solution Explained - Java](https://youtu.be/fKgZiCXb6zs)

*similar to:* 
- 