---
Hardness: Medium
No.: "102"
Solution Type:
  - BFS
Que Type:
  - Binary Tree
Clarity: Low
URL: https://leetcode.com/problems/binary-tree-level-order-traversal/description/
Date: 2025-01-18T15:09
Week:
  - Week 5
Next Review: January 22, 2025
---

## Useful Video Resources

- [Binary Tree Level Order Traversal - YouTube](https://youtu.be/XZnWETlZZ14)
- [Binary Tree Level Order Traversal - BFS - Leetcode 102 - YouTube](https://youtu.be/6ZnyEApgFYg)

## Optimized Solution

```Java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        treverse(res, root, 0);
        return res;
    }

    void treverse(List<List<Integer>> res, TreeNode root, int level) {
        // if we reach a leaf node
        if (root == null) return;

        // if the depth is greater than the number of sublist in result
        // create a new one list
        if (level >= res.size()) res.add(new ArrayList<Integer>());

        // add the value of root, in the sublist of current level
        res.get(level).add(root.val);

        // recursion
        treverse(res, root.left, level + 1);
        treverse(res, root.right, level + 1);
    }
}
```

## Solution

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        if (root == null) return res;
        
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        
        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> currLev = new ArrayList<>();
            for (int i = 0; i < size; i++){
                TreeNode curr = queue.remove();
                currLev.add(curr.val);
                if (curr.left != null) queue.add(curr.left);
                if (curr.right != null) queue.add(curr.right);
            }
            res.add(currLev);
        }
        return res;
    }
}
```

## Key Takeaways