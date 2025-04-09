---
Hardness: Medium
No.: "1765"
Solution Type:
  - BFS
  - Brute Force
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/map-of-highest-peak/description/
Date: 2025-01-22T11:58
Week:
  - 💥Not in Curriculum
Next Review: January 26, 2025
---
Similar to [[0542 - 01 Matrix]]

## Useful Video Resources

## Optimized Solution

uses **Multi Source** [[Breath First Search]]

```Java
class Solution {
    public int[][] highestPeak(int[][] isWater) {
        int n = isWater.length;
        int m = isWater[0].length;
        // int maxDist = n + m;
        int[][] result = new int[n][m];
        Queue<int[]> queue = new LinkedList<>();

        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++) {
                if (isWater[i][j] == 1) {
                    result[i][j] = 0;
                    queue.offer(new int[] { i, j });
                } else
                    result[i][j] = -1;
            }

        // direction array
        int[][] dirs = { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } };
        while (!queue.isEmpty()) {
            int[] curr = queue.poll();
            int x = curr[0];
            int y = curr[1];
            // for each direction from the current
            for (int[] dir : dirs) {
                // new X & Y that needs to be tested
                int testX = x + dir[0];
                int testY = y + dir[1];
                // check if the testX & testY are within bound of grid
                // and the result is only updated for locations that have not been reached
                // this is denoted by -1
                if (testX >= 0 && testX < n && testY >= 0 && testY < m && result[testX][testY] == -1) {
                    // give the testX & testY postion value = current + 1
                    result[testX][testY] = result[x][y] + 1;
                    // add the testX & testY to the queue
                    queue.offer(new int[] { testX, testY });
                }
            }
        }
        return result;
    }
}
```

## Initial Solution

```Java title="Greedy Solution"
class Solution {
    public int[][] highestPeak(int[][] isWater) {
        int n = isWater.length;
        int m = isWater[0].length;
        int maxDist = n + m;
        int[][] result = new int[n][m];

        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++)
                result[i][j] = (isWater[i][j] == 1) ? 0 : maxDist;

        // Forward Pass
        // checks top & left
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (i > 0)
                    result[i][j] = Math.min(result[i][j], result[i - 1][j] + 1);
                if (j > 0)
                    result[i][j] = Math.min(result[i][j], result[i][j - 1] + 1);
            }
        }
        // Backward Pass
        // checks bottom & right
        for (int i = n - 1; i >= 0; i--) {
            for (int j = m - 1; j >= 0; j--) {
                if (i < n - 1)
                    result[i][j] = Math.min(result[i][j], result[i + 1][j] + 1);
                if (j < m - 1)
                    result[i][j] = Math.min(result[i][j], result[i][j + 1] + 1);
            }
        }
        return result;
    }
}
```

## Key Takeaways