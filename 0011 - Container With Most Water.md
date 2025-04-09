---
date: 2025-02-22
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/container-with-most-water/
Hint: Simple 2 Pointer
Clarity: High
Solution Type:
  - Sliding Window
Hardness:
  - Medium
cssclasses:
  - programming-notes
---
### Intuition

- we need to maximize both width & height
- The water that a container can hold is only till the lowest boundary 
- we can calculate `water = width * min(height)`

> [!info] References
> - [Container with Most Water - Leetcode 11 - Python - YouTube](https://youtu.be/UuiTKBwPgAo)
> - [Simple and clear proof/explanation by Stefan Pochmann - LeetCode](https://leetcode.com/problems/container-with-most-water/solutions/6100/simple-and-clear-proof-explanation)

### Follow Up Solution
```java fold title="Better Time Complexicity"
class Solution {
    public int maxArea(int[] height) {
        int currWater = 0, maxWater = 0, l = 0, r = height.length - 1;
        while (l < r) {
            int conHight = Math.min(height[l], height[r]); // Container Height
            int width = r - l;
            currWater = width * conHight;
            maxWater = Math.max(maxWater, currWater);
            // loop both ultill you find a hight that is better than 
            // the current container height
            while ( height[l] <= conHight && l < r )
                l++;
            while ( height[r] <= conHight && l < r )
                r--;
        }
        return maxWater;
    }
}
```
### Initial Solution
```java title="Further Oprimization possible"
class Solution {
    public int maxArea(int[] height) {
        int water = 0,maxWater = -1, l, r;
        for (l = 0, r = height.length-1; l <= r; ){
            int a = height[l];
            int b = height[r];
            int width = r-l;
            water = width * Math.min(a,b);
            maxWater = Math.max(maxWater, water);
            if (a>b) r--;
            else l++;
        }
        return maxWater;
    }
}
```
### Key Takeaways
- Simple [[Sliding Window]]


*similar to:* 
- [[0042 - Trapping Rain Water]]