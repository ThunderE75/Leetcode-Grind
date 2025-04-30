---
Hardness: Easy
No.: "2085"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/count-common-words-with-one-occurrence/description/
Date: 2025-01-13T23:29
Week:
  - 💥Not in Curriculum
Next Review: January 17, 2025
---

## Initial Solution

```Java
class Solution {
    public int countWords(String[] words1, String[] words2) {
        int count=0;
        HashMap<String,Integer>map1=new HashMap<>();
        HashMap<String,Integer>map2=new HashMap<>();

        for (String s : words1)
            map1.put(s, map1.getOrDefault(s,0)+1);
        
        for (String s : words2){
            if (map1.containsKey(s))    
                map2.put(s, map2.getOrDefault(s,0)+1);
        }

        for(String str:map2.keySet())
            if(map1.get(str)==1 && map2.get(str)==1)
                count++;
            
        return count;
    }
}
```

## Key Takeaways

- Create a 2nd filtered Hash Set, only add entries only if they are present in the other