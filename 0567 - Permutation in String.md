---
date: 2025-03-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/permutation-in-string/description/
Hint: 
Clarity: 
Solution Type:
  - Sliding Window
Hardness:
  - Medium
cssclasses:
  - programming-notes
---
## Intuition
- So, [[Sliding Window]], with fixed size of s2
- Permutation implies that the order doesn't matter
- so just the freq of characters must be same 
- and we can use a freq array because the input is limited to lowercase
- use `{java}Arrays.equals()` for array comparison 
## Solution
```java title="Initial Attempt"
class Solution {
    public boolean checkInclusion(String p, String s) {
        if (p.length() > s.length()) return false;

        int[] f1 = new int[26]; 
        int[] f2 = new int[26];
        
        for (int i = 0; i < p.length(); i++) {
            f1[p.charAt(i) - 'a']++;
            f2[s.charAt(i) - 'a']++;
        }
        
        // Sliding Window Tech.
        for (int i = p.length(); i < s.length(); i++) {
            if (Arrays.equals(f1, f2)) return true;
            
            f2[s.charAt(i) - 'a']++;
            f2[s.charAt(i - p.length()) - 'a']--;
        }
        return Arrays.equals(f1, f2);
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. 

*similar to:* 
- When using a frequency array, just use `{java}Arrays.equals()` 
- also keep the edge case in mind where `{java}s1 < s2` 
- 