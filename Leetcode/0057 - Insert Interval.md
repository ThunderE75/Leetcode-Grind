---
Hardness: Medium
No.: "57"
Solution Type:
  - 🧠 Design
Que Type:
  - Array
  - Interval
Clarity: Low
URL: https://leetcode.com/problems/insert-interval/description/
Date: 2024-12-17T22:17
Week:
  - Week 4
Next Review: December 21, 2024
---
## Useful Video Resources

- [Insert Interval - Leetcode 57 - Python - YouTube](https://youtu.be/A8NUOmlwOlM)

## Copied Solution

```Java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List <int[]> result = new ArrayList<>();
        for (int currInterval[] :  intervals) {
            // if start of new > end of current
            // null check should always be in front 
            if (newInterval == null || newInterval[0] > currInterval[1]) {
                // Case 1:  newInterval will be inserted after, 
                //          so add current Interval to result
                result.add(currInterval);
            // if end of new < start of current
            } else if (newInterval[1] < currInterval[0]) {
                // CASE 2:  newInterval will be inserted before
                //          & because there is no overlap, add the current after
                //          & set newInterval to null, to break out the loop 
                result.add(newInterval);
                result.add(currInterval);
                newInterval = null;

            } else {
                // Case 3:  When there is an overlap, 
                //          set the start as min of current & new 
                //          set the end as max of current & new 
                newInterval[0] = Math.min(currInterval[0], newInterval[0]);
                newInterval[1] = Math.max(currInterval[1], newInterval[1]);
            }
        }
        if (newInterval != null) 
            result.add(newInterval);
        
        // What the fuck is this return statement ??
        return result.toArray(new int[result.size()][]);
    }
}
```

## Key Takeaways

- Always have null checks first in a if condition.
- Cases
    1. Current is smaller than new Interval, so add it to result
    2. The new Interval is smaller that current, so add new & then current & set new to null
    3. there is overlap, get & min & max of start & end & add it
- Add all new interval at the end if it’s not null yet  
    (because there was no overlap & the interval)  
    

- Return statement explanation
    
    `**result.toArray(new int[result.size()][])**`:
    
    - The `toArray` method converts the `result` ArrayList into a 2D array.
    - The `new int[result.size()][]` is passed as a template, allowing `toArray` to determine the appropriate type for the resulting array.
    - The elements of `result` are copied into the newly created array.