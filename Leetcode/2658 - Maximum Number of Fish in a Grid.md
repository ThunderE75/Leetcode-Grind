---
Hardness: Medium
No.: "2658"
Solution Type:
  - DFS
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/description/
Date: 2025-01-28T13:57
Next Review: February 1, 2025
---
## Useful Video Resources

- [Maximum Number of Fish in a Grid - Leetcode 2658 - Python - YouTube](https://youtu.be/JhAz6CkRGHI)

## Solution
use [[Depth First Search]]

> [!info] Maximum Number of Fish in a Grid - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/solutions/6337525/beats-100-dfs-matrix-solution-for-leetcode-2658/?envType=daily-question&envId=2025-01-28](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/solutions/6337525/beats-100-dfs-matrix-solution-for-leetcode-2658/?envType=daily-question&envId=2025-01-28)  

```Java
class Solution {
    public int findMaxFish(int[][] grid) {
        int rows = grid.length;
        int cols = grid[0].length;
        int maxFish = 0;

        for (int i = 0; i < rows; i++)
            for (int j = 0; j < cols; j++)
                if (grid[i][j] != 0)
                    maxFish = Math.max(maxFish, dfs(i, j, grid, rows, cols));

        return maxFish;
    }

    public static int dfs(int i, int j, int[][] grid, int rows, int cols) {
        int fish = 0;
        if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] == 0)
            return fish;

        fish += grid[i][j];
        grid[i][j] = 0; // marking it as visited

        fish += dfs(i + 1, j, grid, rows, cols);
        fish += dfs(i - 1, j, grid, rows, cols);
        fish += dfs(i, j + 1, grid, rows, cols);
        fish += dfs(i, j - 1, grid, rows, cols);

        return fish;
    }
}
```

## Key Takeaways

- Traverse cardinal directions using an array `{0,1,0,-1,0}` & loop it till 4th index, and use `i` & `i+1` for cardinal coordinates.

> [!info] Maximum Number of Fish in a Grid - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/solutions/6338241/bfs-vs-dfs-vs-dsu-pattern-explained-100-beats/?envType=daily-question&envId=2025-01-28](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/solutions/6338241/bfs-vs-dfs-vs-dsu-pattern-explained-100-beats/?envType=daily-question&envId=2025-01-28)