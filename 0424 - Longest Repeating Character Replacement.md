---
date: 2025-03-30
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/longest-repeating-character-replacement/description/
Hint: 
Clarity: High
Solution Type:
  - Sliding Window
Hardness:
  - Medium
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- Okay, start from the beginning
- we can use freq. array or a [[Hash Map]] to store the frequency of characters in a window.
- the most dominant character will be the one with highest freq.
- to find ones that are not that, we can do `{java}windowSize-FreqOfDom`  
- we move right on every iteration & left when the non dominant character <= k
## Solution
```java title="Initial Attempt"
class Solution {
    public int characterReplacement(String s, int k) {
        int[] freq = new int[26];
        int a = 0, b = 0;
        int maxSize = 0, maxFreq = 0;
        while (b < s.length()) {
            char c = s.charAt(b);
            freq[c - 'A']++;

            // instead of treversing every time to get higest freq
            // we only check the recently added one vs the curr max
            maxFreq = Math.max(maxFreq, freq[c - 'A']);

            int size = b - a + 1; // +1 because both are inclusive 
            if (size - maxFreq > k) {
                freq[s.charAt(a) - 'A']--;
                a++;
            }

            // window size needs to recalculated after shrinking 
            maxSize = Math.max(maxSize, b - a + 1);
            b++;
        }
        return maxSize;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Longest Repeating Character Replacement - Leetcode 424 - Python](https://youtu.be/gqXU1UyA8pk)
> 2. 

*similar to:* 
- [[0003 - Longest Substring Without Repeating Characters]]
- 