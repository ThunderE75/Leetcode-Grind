---
Hardness: Easy
No.: "409"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/longest-palindrome/description/
Date: 2024-11-11T20:20
Week:
  - Week 2
Next Review: November 15, 2024
---

## Useful Resources

- [LeetCode Longest Palindrome Solution Explained - Java - YouTube](https://youtu.be/a_3XDW9P47E)

## Initial Solution

```Java
class Solution {
    public int longestPalindrome(String s) {
        int len = 0;
        boolean hasOdd = false;
        char[] arr = s.toCharArray();
        HashMap<Character, Integer> map = new HashMap<>();
		
        // storing character occourances
        for (char c : arr) {
            map.put(c, (map.getOrDefault(c, 0) + 1));
        }
		
        for (int i : map.values()) {
            // adding all largest even part of i
            len += (i / 2) * 2;
            // find if there is an odd value left
            if (i % 2 == 1) 
                hasOdd = true;
        }
        return len = (hasOdd) ? len + 1 : len;
    }
}
```

## Thinking

- I need to create the longest palindrome possible from the string given
- don’t need points, just need a hash table
    - we don’t need to use all characters
    - we can use hash table to store the occurrence of each character
    - we can gradually remove 2 from the hash value & add it to the length
    - we can continue this until (`map.value ≤ 1`) or (`map.value % 2 != 1`)
    - and just add 1 to the length, cause only 1 character can of odd number