---
date: 2024-11-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/maximum-depth-of-binary-tree/description/
Hint: use Math.max()
Clarity: Medium
Solution Type:
  - DFS
  - Recursion
Hardness:
  - Easy
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- to get max depth we would need to do a [[Depth First Search|DFS]] 
- we can use recursion but we need to only add +1 for each depth
- we can check if both left and right exist, but how can we which path to proceed to
- i don't know where to start.
## Solution
```java title="Initial Attempt"
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
}
```

```java fold title="Recursive Approch using Global variable"
class Solution {
    int maxDepth=0;
    public int maxDepth(TreeNode root) {
        dive (root, 1);
        return maxDepth;
    }

    void dive(TreeNode root, int level){
        if(root == null) return;
        maxDepth = Math.max(maxDepth, level);
        dive(root.left, level + 1);
        dive(root.right, level + 1);
    }
}
```
## Key Takeaways
- whenever using recursion, don't assign variables, because they reset
- and in cases of tree, a common base case is `{java}if(root==null) return null;`  

> [!info] References
> 1. [Maximum Depth of Binary Tree - 3 Solutions - Leetcode 104 - Python](https://youtu.be/hTM3phVI6YQ) 

*similar to:* 
- [[0110 - Balanced Binary Tree]] 