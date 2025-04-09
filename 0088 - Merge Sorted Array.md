---
date: 2025-03-26
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/merge-sorted-array/description/
Hint: Start and the end
Clarity: Crystal
Solution Type:
  - 2 Pointer
Hardness:
  - Easy
cssclasses:
  - programming-notes
---
### Intuition
- we have length of both inputs, we can go backwards
- to find the last actual element of `nums1`, we can perform `m-n`
- and compare both the list backwards
  ![[4815aa40-1c65-4e21-b6e5-7cc2cbe8925c_1743006335.0646713.gif]]

> [!info] References
> - [Write Up](https://leetcode.com/problems/merge-sorted-array/solutions/6582765/simple-java-solution-visualization-beats-4hhd)
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int curr = nums1.length - 1;
        while (m > 0 && n > 0)
            nums1[curr--] = (nums1[m-1] >= nums2[n-1]) ? nums1[--m] : nums2[--n];
        while(m > 0)
            nums1[curr--] = nums1[--m];
        while(n > 0)
            nums1[curr--] = nums2[--n];
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 