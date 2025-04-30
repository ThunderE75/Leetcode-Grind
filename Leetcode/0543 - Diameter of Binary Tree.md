---
Date: 2025-04-06
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/diameter-of-binary-tree/description/
Hint: 
Clarity: Low
Solution Type: 
Hardness: Easy
cssclasses:
  - programming-notes
  - no_url_underline
---

## Intuition
- After watching ref 1
- we get the max depth of both left and right sub tree,
- and them to get the diameter,
- and repeat for each node
## Solution
```java title="Initial Attempt"
class Solution {

    public int diameterOfBinaryTree(TreeNode root) {
        if (root == null) return 0;
        int leftHeight = getHeight(root.left);
        int rightHeight = getHeight(root.right);
        int currDist = leftHeight + rightHeight;
        // a bit Unintuitive
        int subtreeMax = Math.max(diameterOfBinaryTree(root.left), diameterOfBinaryTree(root.right));
        return Math.max(currDist, subtreeMax);
    }

    int getHeight(TreeNode root) {
        if (root == null)
            return 0;
        return 1+ Math.max(getHeight(root.left), getHeight(root.right));
    }
}
```

```java fold title="Most Optimized Variation"
class Solution {
    int maxDia = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        if (root == null) return 0;
        getDepth(root);
        return maxDia;
    }

    int getDepth(TreeNode root) {
        if (root == null) return 0;
        int leftDepth = getDepth(root.left);
        int rightDepth = getDepth(root.right);
        int currDia = leftDepth + rightDepth;
        maxDia = Math.max(maxDia, currDia);
        return 1 + Math.max(leftDepth, rightDepth);
    }
}
```
## Key Takeaways
- 

> [!info] References
> 1. [Neetcode - Diameter of Binary Tree - Leetcode 543 - Python](https://youtu.be/K81C31ytOZE) 

*similar to:* 
- [[0104 - Maximum Depth of Binary Tree]] 