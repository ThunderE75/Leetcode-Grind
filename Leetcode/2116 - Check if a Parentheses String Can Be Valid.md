---
Hardness: Medium
No.: "2116"
Solution Type:
  - Stack
Que Type:
  - String
Clarity: Low
URL: https://leetcode.com/problems/check-if-a-parentheses-string-can-be-valid/description/
Date: 2025-01-12T13:35
Week:
  - 💥Not in Curriculum
Next Review: January 16, 2025
---
## Useful Video Resources

- [Check if a Parentheses String Can Be Valid - Leetcode 2116 - Python - YouTube](https://youtu.be/KMIIGDiXLhY)

## Optimized Solution

> [!info] Check if a Parentheses String Can Be Valid - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/check-if-a-parentheses-string-can-be-valid/solutions/6267067/simple-balance-2-methods-detailed-solution/?envType=daily-question&envId=2025-01-12](https://leetcode.com/problems/check-if-a-parentheses-string-can-be-valid/solutions/6267067/simple-balance-2-methods-detailed-solution/?envType=daily-question&envId=2025-01-12)  

```Java
class Solution {
    public boolean canBeValid(String s, String locked) {
        // just valid paranthesis;
        // check both the string & the loked status itself
        if (s.length() % 2 != 0)
            return false;

        Stack<Integer> stkOpen = new Stack<>(); // to track Open Parentheses
        Stack<Integer> stkUnlock = new Stack<>(); // to track unlocked index

        // Traverse through the string
        // Tracking the index of Open Parentheses & unlocked index
        for (int i = 0; i < s.length(); i++) {
            if (locked.charAt(i) == '0')
                stkUnlock.push(i);
            else if (s.charAt(i) == '(')
                stkOpen.push(i);
            else { // when s.charAt(i)==')'
                if (!stkOpen.isEmpty())
                    stkOpen.pop();
                else if (!stkUnlock.isEmpty())
                    stkUnlock.pop();
                else
                    return false;
            }
        }

        // Match remaining open parentheses
        while (!stkUnlock.isEmpty() && !stkOpen.isEmpty()
                && stkOpen.peek() < stkUnlock.peek()) {
            // We need to conform that the index of open Parentheses
            // is smaller (i.e. after) that index of wild card (unlocked index)
            stkOpen.pop();
            stkUnlock.pop();
        }

        // If there are unmatched open parentheses, return false
        return stkOpen.isEmpty() && stkUnlock.size() % 2 == 0;
    }
}
```

## Key Takeaways