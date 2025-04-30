---
Date: 2025-03-03
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/partition-array-according-to-given-pivot/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition

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
    public int[] pivotArray(int[] nums, int pivot) {
        int n = nums.length;
        int[] res = new int[n];
        int[] smaller = new int[n];
        int[] bigger = new int[n];
        int count=0, s=0, b=0;

        for(int i=0; i<n; i++){
            if(nums[i] < pivot)
                smaller[s++] = nums[i];
            else if (nums[i] > pivot)
                bigger[b++] = nums[i];
            else count++;
        }
        Arrays.fill(res,pivot);
        System.arraycopy(smaller,0,res, 0,s);
        System.arraycopy(bigger,0,res, s+count,b);
        // res = Arrays.copyOf()
        // ArrayList <Integer> res = new ArrayList<>();
        // for(int i : smaller)
        //     res.add(i);
        // for(int i=0; i< count;i++)
        //     res.add(pivot);
        // for(int i : bigger)
        //     res.add(i);
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 