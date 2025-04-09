---
Hardness: Medium
No.: "2657"
Solution Type:
  - Hash Map / Set
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/find-the-prefix-common-array-of-two-arrays/description/
Date: 2025-01-14T17:42
Week:
  - 💥Not in Curriculum
Next Review: January 18, 2025
---
## Optimized Solution

```Java
class Solution {
    public int[] findThePrefixCommonArray(int[] A, int[] B) {
        int common = 0;
        int[] res = new int[A.length];
        int[] freq = new int[A.length + 1];
        for (int i = 0; i < A.length; i++) {
            if (++freq[A[i]] == 2) common++;
            if (++freq[B[i]] == 2) common++;
            res[i] = common;
        }
        return res;
    }
}
```

## Initial Solution

```Java
class Solution {
    public int[] findThePrefixCommonArray(int[] A, int[] B) {
        int count = 0;
        int[] res = new int[A.length];
        int[] freq = new int[A.length+1];
        Arrays.fill(res,0);
        Arrays.fill(freq,0);
        for (int i = 0; i < A.length; i++){
            freq[A[i]]++;
            freq[B[i]]++;
            for (int j : freq)
                if (j > 1)
                    count+=1;
            res[i] = count;
            count=0;
        }
        return res;
    }
}
```