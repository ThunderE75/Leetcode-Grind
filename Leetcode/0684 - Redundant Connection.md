---
Hardness: Medium
No.: "684"
URL: https://leetcode.com/problems/redundant-connection/description/
Date: 2025-01-29T17:43
Next Review: February 2, 2025
---

## Useful Video Resources

- [Disjoint Set \| UNION and FIND - YouTube](https://youtu.be/eTaWFhPXPz4)
- [Disjoint set UNION by RANK and Path Compression - YouTube](https://youtu.be/kaBX2s3pYO4)

## Solution
using [[Disjoint Set Union]]

> [!question] Redundant Connection - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/redundant-connection/solutions/2278999/union-find-concept-and-multiple-solutions-java/?envType=daily-question&envId=2025-01-29](https://leetcode.com/problems/redundant-connection/solutions/2278999/union-find-concept-and-multiple-solutions-java/?envType=daily-question&envId=2025-01-29)  

```Java
class Solution {
    int[] parent;
    public int[] findRedundantConnection(int[][] edges) {
        parent = new int[edges.length + 1];
        // Setting the parrent for each node as itself
        for (int i = 1; i < edges.length; i++)
            parent[i] = i;
        for (int[] edge : edges) {
            // if both nodes are a child of common absolute root
            if (find(edge[0]) == find(edge[1]))
                return edge;
            union(edge[0], edge[1]);
        }
        return new int[] { -1, -1 };

    }

    public int find(int node) {
        // loop until you find a node that points to itself
        while (parent[node] != node)
            node = parent[node];
        return node;
    }

    public void union(int a, int b) {
        // getting the absolute root of both nodes
        int aRoot = find(a);
        int bRoot = find(b);
        if (aRoot != bRoot)
            parent[bRoot] = aRoot;
    }
}
```

## Key Takeaways

- Union Find Method
- Can be optimized further, by using ranked unions