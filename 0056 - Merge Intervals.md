---
No.: "56"
URL: https://leetcode.com/problems/merge-intervals/
Date: 2024-12-19T19:08
Week:
  - Week 4
Next Review: December 23, 2024
---
## Useful Video Resources

- [https://youtu.be/qKczfGUrFY4](https://youtu.be/qKczfGUrFY4)

## Solution

```Java
class Solution {
    public int[][] merge(int[][] intervals) {
        // Sort intervals by the start time
        Arrays.sort(intervals, (curr, next) -> Integer.compare(curr[0], next[0]));

        List<int[]> res = new ArrayList<>();
        for (int i = 0; i < intervals.length; i++) {
            // Check if we're not at the last interval
            if (i + 1 < intervals.length && intervals[i][1] < intervals[i + 1][0]) {
                // No overlap, just add the current interval
                res.add(intervals[i]);
            } else if (i + 1 < intervals.length && intervals[i][1] >= intervals[i + 1][0]) {
                // Overlapping intervals, merge them
                int[] newInterval = new int[] {
                    Math.min(intervals[i][0], intervals[i + 1][0]),
                    Math.max(intervals[i][1], intervals[i + 1][1])
                };
                res.add(newInterval);
                i++; // Skip the next interval since it's merged
            } else if (i + 1 == intervals.length) {
                // Add the last interval when we reach the end
                res.add(intervals[i]);
            }
        }
        // Convert the result list to a 2D array and return
        return res.toArray(new int[res.size()][]);
    }
}
```

## Key Takeaways