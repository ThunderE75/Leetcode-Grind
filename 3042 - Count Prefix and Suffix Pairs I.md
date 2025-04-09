---
Hardness: Easy
No.: "3042"
Solution Type:
  - 2 Pointer
Que Type:
  - Array
  - String
Clarity: Crystal
URL: https://leetcode.com/problems/count-prefix-and-suffix-pairs-i/description/
Date: 2025-01-08T14:33
Week:
  - 💥Not in Curriculum
---
> [!important] POTD → January 08, 2025

## Useful Video Resources

- [Count Prefix and Suffix Pairs I & II - Leetcode 3042 & 3045 - Python - YouTube](https://youtu.be/zQrtsvo8lgM)

## Initial Solution

```Java
class Solution {
    public static int countPrefixSuffixPairs(String[] words) {
        int count = 0;
        for (int i = 0; i < words.length; i++) {
            for (int j = i+1; j < words.length; j++) {
                count += isPrefixAndSuffix(words[i], words[j]) ? 1 : 0;
            }
        }
        return count;
    }
	
    public static boolean isPrefixAndSuffix(String str1, String str2) {        
        return (str2.startsWith(str1) && str2.endsWith(str1));
    }
}
```