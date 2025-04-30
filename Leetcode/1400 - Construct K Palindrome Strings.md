---
Hardness: Medium
No.: "1400"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/construct-k-palindrome-strings/description/
Date: 2025-01-11T22:52
Week:
  - 💥Not in Curriculum
Next Review: January 15, 2025
---

## Useful Video Resources

- [https://youtu.be/D00qGvqmqN0](https://youtu.be/D00qGvqmqN0)

## Initial Solution

```Java
class Solution {
    public boolean canConstruct(String s, int k) {
        boolean temp;
        HashSet<Character> set = new HashSet<>();
        if (k > s.length()) return false;
        else {
            for (char c : s.toCharArray())
                if (set.contains(c))
                    set.remove(c);
                else
                    set.add(c);
            if (set.size() > k) return false;
        }
        return true;
    }
}
```

## Key Takeaways