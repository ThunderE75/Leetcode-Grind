---
date: 2025-03-02
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/merge-two-2d-arrays-by-summing-values/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- Ways to solve
	- Hashmap -> iterate one by one on each input array and store 
	- Since they are sorted, run one pointer for each
- We can either use Array(n+m) or an ArrayList

> [!info] References
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
    public int[][] mergeArrays(int[][] nums1, int[][] nums2) {
        int n = nums1.length;
        int m = nums2.length;
        int[][] res = new int[n+m][2];
        
        int i = 0, j = 0, k = 0; 
        while (j < n && k < m ) {
            if (nums1[j][0] == nums2[k][0]) {
                res[i][0] = nums1[j][0];
                res[i][1] = nums1[j++][1] + nums2[k++][1];
            } else if (nums1[j][0] < nums2[k][0]) {
                res[i][0] = nums1[j][0];
                res[i][1] = nums1[j++][1];
            } else { // if (nums1[j][0] > nums2[k][0])
                res[i][0] = nums2[k][0];
                res[i][1] = nums2[k++][1];
            }
            i++;
        }
        while (j<n){
            res[i][0] = nums1[j][0];
            res[i][1] = nums1[j++][1];
            i++;
        }
        while(k < m){
            res[i][0] = nums2[k][0];
            res[i][1] = nums2[k++][1];
            i++;
        }
        return Arrays.copyOf(res, i);
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 