---
Hardness: Easy
No.: "383"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: Medium
URL: https://leetcode.com/problems/ransom-note/description/
Date: 2024-11-10T19:34
Week:
  - Week 2
Next Review: November 14, 2024
---
## Optimized Solution

```Java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] dict = new int[26];
        for(char c : magazine.toCharArray())
            dict[c - 'a']++;
        for(char ch : ransomNote.toCharArray()){
            dict[ch - 'a']--;
            if(dict[ch - 'a'] == -1)
                return false;
        }
        return true;
    }
}
```

[https://leetcode.com/problems/ransom-note/solutions/5644265/easiest-faster-lesser-c-python3-java-c-python-c-explained-beats](https://leetcode.com/problems/ransom-note/solutions/5644265/easiest-faster-lesser-c-python3-java-c-python-c-explained-beats)

## Initial Solution

Very Similar to [[0242 - Valid Anagram]]

```Java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        char[] ranArr = ransomNote.toCharArray(); 
        char[] magArr = magazine.toCharArray(); 
        HashMap <Character, Integer> map = new HashMap<>();
		
        if(ransomNote.length()>magazine.length()) return false;
		
        for(char c : ranArr)
            map.put(c, (map.getOrDefault(c,0)+1));
        
        for(char c : magArr)
            map.put(c, (map.getOrDefault(c,0)-1));
		
        for (int i : map.values())
            if(i>0) return false;
        
        return true;
    }
}
```
