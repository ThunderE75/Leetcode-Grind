---
Hardness: Easy
No.: "1422"
Solution Type:
  - Sliding Window
Que Type:
  - Array
Clarity: High
URL: https://leetcode.com/problems/maximum-score-after-splitting-a-string/description/
Date: 2025-01-05T14:57
Week:
  - 💥Not in Curriculum
Next Review: January 9, 2025
---
> [!important] POTD → January 1, 2025

## Useful Video Resources

- [Fetching Title#4c3u](https://youtu.be/eJx-Cyc6KRQ)

## Solution

```Java
class Solution {
    public int maxScore(String s) {
        int left = 0; // increases with 0
        int right = 0; // increases with 1
        int res = 0;
        char[] arr = s.toCharArray();
        for (char c : arr){
            if (c=='1') 
                right++;
        }
        for (int i = 0; i< arr.length-1; i++){
            if(arr[i] == '1')
                right--;
             else
                left++;
            res = Math.max(res, (right+left));
        }
        return res;
    }
}
```