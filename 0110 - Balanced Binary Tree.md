---
Hardness: Easy
No.: "110"
Solution Type:
  - DFS
  - Recursion
Que Type:
  - Binary Tree
  - Tree
Clarity: Low
URL: https://leetcode.com/problems/balanced-binary-tree/description/
Date: 2024-11-07T00:19
Week:
  - Week 2
Next Review: November 11, 2024
---
## Intuition
- Okay, balanced means, the max height of subtrees can't differ more than 1 
- 
## Solution
```java title="Initial Attempt"
class Solution {
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        int left = getDepth(root.left);
        int right = getDepth(root.right);
        if (Math.abs(left - right) > 1)
            return false;
        return isBalanced(root.left) && isBalanced(root.right);
    }

    int getDepth(TreeNode root) {
        if (root == null) return 0;
        return 1 + Math.max(getDepth(root.left), getDepth(root.right));
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Balanced Binary Tree - Leetcode 110 - Python](https://youtu.be/QfJsau0ItOY)

*similar to:* 
- [[0104 - Maximum Depth of Binary Tree]] 



























## Assisted Solution

```Java
class Solution {
    boolean res = true;
    public boolean isBalanced(TreeNode root) {
        height(root);
        return res;
    }
    public int height(TreeNode root){

        // As soon as the result becomes false, it quits recursion
        if (!res) return 0;

        // If root is an leaf node
        if (root == null) return 0;

        // Recursivelly getting the height of the tree
        int leftH = height(root.left);
        int rightH = height(root.right);

        // Check if difference is greater than 1 in either direction
        if (Math.abs(leftH - rightH) > 1)
            res = false;
        
        // Return the depth of the current node = Maximum depth of its subtrees + 1
        return Math.max(leftH, rightH) + 1 ;
    }
}
```

## Initial Solution

```Java
class Solution {
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true; 
        if (root.right != null ){
            isBalanced(root.right);
        }else if (root.left != null ){
            isBalanced(root.left);
        }
        if(root.left == null && root.right == null) return true;
        return false;
    }
}
```