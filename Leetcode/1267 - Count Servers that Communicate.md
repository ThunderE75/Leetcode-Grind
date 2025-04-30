---
Hardness: Medium
No.: "1267"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: High
URL: https://leetcode.com/problems/count-servers-that-communicate/description/
Date: 2025-01-23T21:02
Week:
  - 💥Not in Curriculum
Next Review: January 27, 2025
---

## Useful Video Resources

- [https://youtu.be/meTbkgqNNYM](https://youtu.be/meTbkgqNNYM)

## Solution

```Java
class Solution {
    public int countServers(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] rowC = new int[m];
        int[] colC = new int[n];
        int res = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                rowC[i] += grid[i][j];
                colC[j] += grid[i][j];
            }
        }

        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (grid[i][j] == 1 && (rowC[i] > 1 || colC[j] > 1))
                    res++;

        return res;
    }
}
```

## Key Takeaways