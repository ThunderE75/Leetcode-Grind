---
Hardness:
  - Hard
No.: "42"
Solution Type:
  - 2 Pointer
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/trapping-rain-water/description/
Date: 2025-01-19T16:14
Next Review: January 23, 2025
---
## Intuition 

- 

## Useful Video Resources

- [Trapping Rain Water - Google Interview Question - Leetcode 42 - YouTube](https://youtu.be/ZI2z5pq0TqA) 
- 

## Solution

```Java
class Solution {
    public int trap(int[] height) {
        int water = 0;
        int l = 0, r = height.length - 1;
        int lmax = Integer.MIN_VALUE;
        int rmax = Integer.MIN_VALUE;

        while (l < r) {
            lmax = Math.max(lmax, height[l]);
            rmax = Math.max(rmax, height[r]);
            if (lmax < rmax)
                water += lmax - height[l++];
            else
                water += rmax - height[r--];
        }
        return water;
    }
}
```

## Key Takeaways

> [!info] Trapping Rain Water - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/trapping-rain-water/solutions/4158470/3-lines-solution-with-explaination/](https://leetcode.com/problems/trapping-rain-water/solutions/4158470/3-lines-solution-with-explaination/)  

- 2 points at both ends of the array
- we take the max of the left boundary & same for right
- If the smaller tower is at the left end, water trapped would be dependent on the tower's height in the direction from left to right.
- Similarly, if the tower at the right end is smaller, water trapped would be dependent on the tower's height in the direction from right to left.
- So we first calculate water trapped on the smaller tower among height[left] and height[right] and move the pointer associated with the smaller tower.
- Loop will run till the left pointer doesn't cross the right pointer.