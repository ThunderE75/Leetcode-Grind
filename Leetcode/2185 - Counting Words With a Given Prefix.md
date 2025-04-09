---
Hardness: Easy
No.: "2185"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Crystal
URL: https://leetcode.com/problems/counting-words-with-a-given-prefix/description/
Date: 2025-01-09T14:07
Week:
  - 💥Not in Curriculum
---
> [!error] POTD → January 09, 2025

## Initial Solution

```Java
class Solution {
    public int prefixCount(String[] words, String pref) {
        int count = 0;
        for (String s : words)
            count += s.startsWith(pref) ? 1 : 0;
        return count;
    }
}
```