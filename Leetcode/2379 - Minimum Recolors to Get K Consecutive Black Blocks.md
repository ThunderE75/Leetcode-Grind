---
Date: 2025-03-08
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/minimum-recolors-to-get-k-consecutive-black-blocks/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- we can use the [[Sliding Window]] technique 
- 


> [!info] References
> - [Minimum Recolors to Get K Consecutive Black Blocks - Leetcode 2379 - YouTube](https://www.youtube.com/watch?v=cWz4_zUegxE)
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java
class Solution {
    public int minimumRecolors(String blocks, int k) {
        int n = blocks.length();
        int whites = 0;

        // Initial count of 'White' in the first window
        for (int i = 0; i < k; i++)
            if (blocks.charAt(i) == 'W')
                whites++;

        int res = whites;

        // Sliding
        for (int i = k; i < n; i++) {
            if (blocks.charAt(i) == 'W')
                whites++;
            if (blocks.charAt(i - k) == 'W')
                whites--;
            res = Math.min(res, whites);
        }
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 