---
Hardness: Easy
No.: GFG
URL: https://www.geeksforgeeks.org/problems/implement-strstr/0
Date: 2024-12-24T20:39
Week:
  - GFG
Next Review: December 28, 2024
---
## Initial Solution

```Java
class Solution {
    // Function to locate the occurrence of the string x in the string s.
    int firstOccurence(String txt, String pat) {
        // Your code here
        if (txt == null || pat == null || pat.length() > txt.length())
            return -1;
        
        int idx=-1;
        int chk=0;
        char[] base = txt.toCharArray();
        char[] search = pat.toCharArray();
        
        for (int i = 0; i < base.length; i++) {
            if (base[i] == search[chk]) {
                if (chk == 0) 
                    idx = i; // Record the starting index of the match
                chk++; // Move to the next character in the pattern
                if (chk == search.length) 
                    return idx; // Entire pattern matched
            } else {
                // Reset on mismatch
                if (chk > 0)
                    i = i - chk; // Backtrack to the character after the failed match
                idx = -1; // Reset starting index
                chk = 0; // Reset pattern pointer
            }
        }
        return -1;
    }
}
```