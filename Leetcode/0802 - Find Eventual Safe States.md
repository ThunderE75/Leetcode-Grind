---
Hardness: Medium
No.: "802"
Solution Type:
  - DFS
Que Type:
  - Graph
Clarity: Low
URL: https://leetcode.com/problems/find-eventual-safe-states/description
Date: 2025-01-24T18:25
Week:
  - 💥Not in Curriculum
Next Review: January 28, 2025
---
## Useful Video Resources

- [https://youtu.be/wciKkM3g3wQ](https://youtu.be/wciKkM3g3wQ)

## Solution

> [!info] Find Eventual Safe States - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/find-eventual-safe-states/solutions/6322210/dfs-based-cycle-detection-to-find-safe-nodes-in-a-directed-graph-intuitive-solution/?envType=daily-question&envId=2025-01-24](https://leetcode.com/problems/find-eventual-safe-states/solutions/6322210/dfs-based-cycle-detection-to-find-safe-nodes-in-a-directed-graph-intuitive-solution/?envType=daily-question&envId=2025-01-24)  

```Java
class Solution {
    public boolean dfs(int[][] graph, int node, int[] state){
        if(state[node] > 0) 
            return state[node] == 2; 

        state[node] = 1;

        for (int next : graph[node])
            if (state[next] == 1 || !dfs(graph, next, state))
                return false;
        
        state[node] = 2;
        return true;

    }

    public List<Integer> eventualSafeNodes(int[][] graph) {
        int n = graph.length;
        int[] state = new int[n];
        List<Integer> res = new ArrayList<>();

        for (int i = 0; i < n; i++)
            if (dfs(graph, i, state))
                res.add(i);

        return res;
    }
}
```

## Key Takeaways