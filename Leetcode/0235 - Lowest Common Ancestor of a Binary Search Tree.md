---
Hardness: Easy
No.: "235"
Solution Type:
  - Recursion
Que Type:
  - Binary Tree
  - Tree
Clarity: Medium
URL: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/
Date: 2024-11-06T22:58
Week:
  - Week 1
Next Review: November 10, 2024
---

## Intuition
- Okay we need to understand the properties of [[Binary Search Tree]]
- All cases
	1. If p and q are smaller than root value, search in left sub-tree.
	2. If p and q are greater, search in right sub-tree.
	3. If p is smaller and q is greater or vice-versa, return root node.
## Solution
```java title="Initial Attempt"
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null) return null;

        if (root.val < p.val && root.val < q.val)
            return lowestCommonAncestor(root.right, p, q);
        else if (root.val > p.val && root.val > q.val)
            return lowestCommonAncestor(root.left, p, q);
        return root;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Lowest Common Ancestor of a Binary Search Tree - Leetcode 235 - Python - YouTube](https://youtu.be/gs2LMfuOR9k)
> 2. [LeetCode 235. Lowest Common Ancestor of a Binary Search Tree (Algorithm Explained) - YouTube](https://youtu.be/6POfA8fruxI)

*similar to:* 
- 