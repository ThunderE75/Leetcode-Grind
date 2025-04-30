---
Date: 2025-01-05
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/longest-substring-without-repeating-characters/description/
Hint: HashSet Sliding window
Clarity: High
Solution Type:
  - Sliding Window
Hardness: Medium
cssclasses:
  - programming-notes
  - no_url_underline
---

## Intuition
- Simple [[Sliding Window]], w/ hashset.
- Remove first char as we move when encountering a dupe.
## Solution
```java title="Initial Attempt"
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int a = 0 , b = 0;
        int max = 0;
        HashSet<Character> set = new HashSet<>();
        while(b < s.length()){
            char curr = s.charAt(b);
            if(!set.contains(curr)){
                set.add(curr);
                max = Math.max(max, set.size());
                b++;
            } else {
                set.remove(s.charAt(a));
                a++;
            }
        }
        return max;
    }
}
```

```java fold title=""

```
## Key Takeaways
- in sliding window, keep `a` & `b` out of the loop & use a `while` loop

> [!info] References
> 1. [Neetcode - 3. Longest Substring Without Repeating Characters - Leetcode - Python](https://youtu.be/wiGpQwVHdE0)
> 2. [Nick White - Longest Substring Without Repeating Characters Solution Explained - Java](https://youtu.be/3IETreEybaA)

*similar to:* 
- [[0424 - Longest Repeating Character Replacement]]