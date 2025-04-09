---
Hardness: Easy
No.: "1408"
Solution Type:
  - Brute Force
Que Type:
  - Array
  - String
Clarity: High
URL: https://leetcode.com/problems/string-matching-in-an-array/description/
Date: 2025-01-07T15:41
Week:
  - 💥Not in Curriculum
Next Review: January 11, 2025
---
## Useful Video Resources

- [String Matching in an Array - Leetcode 1408 - Python - YouTube](https://youtu.be/7K2BjgjCFDo)

> [!important] Daily Leetcode question → January 07. 2025
> 
> You can use `Knuth Morris Pratt` or `Rabin Karp` for this question

## Initial Solution [Brute Force Approach]

```Java
// Brute Force Approach
class Solution {
    public List<String> stringMatching(String[] words) {
        List<String> res = new ArrayList<>();
        for(int i = 0; i< words.length; i++)
            for(int j = 0; j < words.length; j++)
                if (i !=j && words[j].contains(words[i])){
                    res.add(words[i]);
                    break;
                }
        return res;
    }
}
```

## Key Takeaways

- Time Complexity = $O(n~.~m)$