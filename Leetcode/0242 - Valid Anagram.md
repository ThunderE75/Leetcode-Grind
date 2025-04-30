---
Hardness: Easy
No.: "242"
Solution Type:
  - Brute Force
  - Hash Map / Set
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/valid-anagram/description/
Date: 2024-11-05T00:43
Week:
  - Week 1
  - 🚀 Neetcode
Session 1: Mid
Next Review: November 15, 2024
SR Notes:
  - "[[1-242]]"
---

## Initial Solution

```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length()) return false;
        HashMap<Character, Integer> map = new HashMap<>();
        char[] sArr = s.toCharArray(); 
        char[] tArr = t.toCharArray(); 
        for(char c : sArr){
            map.put(c,map.getOrDefault(c,0)+1);
        }
        for(char c : tArr){
            map.put(c,(map.getOrDefault(c,0)-1));
        }
        for(int i:map.values()){
            if (i!=0) return false;
        }
        return true;
    }
}
```