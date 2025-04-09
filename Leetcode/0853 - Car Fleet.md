---
date: 2025-02-27
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/car-fleet/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- 

> [!info] References
> - [Car Fleet Solution - Neetcode](https://neetcode.io/problems/car-fleet)
> - [Car Fleet Solution - LeetCode](https://leetcode.com/problems/car-fleet/solutions/6066400/finding-the-number-of-car-fleets-using-stack-79ms)
> - [Car Fleet Solution by LEE - LeetCode](https://leetcode.com/problems/car-fleet/solutions/139850/c-java-python-straight-forward)
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java title="uses Monotonic Stack"
class Solution {
    public int carFleet(int target, int[] pos, int[] speed) {
        int n = pos.length;
        if (n == 1)
            return 1;
        int[][] cars = new int[n][2];
        for (int i = 0; i < n; i++) {
            cars[i][0] = pos[i];
            cars[i][1] = speed[i];
        }
        // Sorting the array based on the position in non increasing order
        Arrays.sort(cars, (a, b) -> b[0] - a[0]);

        Stack<Double> stk = new Stack<>();
        for(int i = 0 ; i < n; i ++){
            // Time = distance / speed
            double time = (double)(target-cars[i][0])/cars[i][1];
            if (stk.isEmpty() || stk.peek() < time )
                stk.push(time);
        }
        return stk.size();
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 