---
Hardness: Medium
No.: "2017"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/grid-game/description
Date: 2025-01-21T20:53
Week:
  - 💥Not in Curriculum
Next Review: January 25, 2025
---

## Useful Video Resources

- [Grid Game \| Leetcode 2017 - YouTube](https://youtu.be/qA7yyNI2xKM)
- [Grid Game - Leetcode 2017 - Python - YouTube](https://youtu.be/B90kG-ZlptE)

## Solution

```Java
class Solution {
    public long gridGame(int[][] grid) {
        long topSum = 0;
        long btmSum = 0;
        long result = Long.MAX_VALUE;

        for (int i : grid[0])
            topSum += i;

        // We try every partition point (i)
        for (int i = 0; i < grid[0].length; ++i) {
            // we remove the current partition point from the topSum
            topSum -= grid[0][i];
            result = Math.min(result, Math.max(topSum, btmSum));
            // we add the current partition point in the btmSum
            btmSum += grid[1][i];
        }

        return result;
    }
}
```

## Key Takeaways

- Use long to avoid overflow.

## Working

- take out the total sum of the top row
- at the point of partition (where the robot goes to the bottom row)
- it divides the grid into 2 parts `Top Right` & `Bottom Left`
- we iterate over every possible partition point &
    - remove from the `topSum`
    - calculate the result 
        
``` result = Minimum( Result , MAX( TopSum , BottomSum ) )```

- Because Robot 2 will try to get the MAX frame
	- `MAX( TopSum , BottomSum )`
- But Robot 1 will try to minimize the result
	- `Minimum( Result , MAX( TopSum , BottomSum ) )`
- add to the `bottomSum` (for the next iteration)