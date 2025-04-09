---
date: 2025-02-18
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/longest-consecutive-sequence/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition

> [!info] References
> - [128. Longest Consecutive Sequence - Neetcode](https://youtu.be/P6RZZMu_maU)
> - [Union Find - Longest Consecutive Sequence - LeetCode](https://leetcode.com/problems/longest-consecutive-sequence/solutions/3780530/java-union-find-hashmap-o-n-time-complexity)
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java title="TLE Hell"
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int i : nums)
            set.add(i);

        int maxChain = 0;
        //for (int i : nums) {
        for (int i : set) { // iterate over set, not the input, otherwise TLE
            int chain = 1;
            if (!set.contains(i - 1)) { // if true -> it's a start
                chain = 1;
                while (set.contains(i + chain))
                    chain++;
            }
            maxChain = Math.max(maxChain, chain);
        }
        return maxChain;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 