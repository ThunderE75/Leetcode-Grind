---
Hardness: Medium
No.: "49"
Solution Type:
  - Hash Map / Set
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/group-anagrams/description/
Date: 2025-01-19T15:59
Week:
  - 💥Not in Curriculum
  - 🚀 Neetcode
Next Review: January 23, 2025
Remarks: Approach → Take out string, char array, sort, convert to string, use this string as a key, then push all the related element to key
---
## Useful Video Resources

- [Group Anagrams - Categorize Strings by Count - Leetcode 49 - YouTube](https://youtu.be/vzdNOK2oB2E)
- 

## Solution

```Java fold title="Try Yourself First"
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();

        for (String s : strs){
            char[] carr = s.toCharArray();
            Arrays.sort(carr);
            String ss = new String(carr);
            if (!map.containsKey(ss)) 
                map.put(ss, new ArrayList<>());
            map.get(ss).add(s);
        }        
        return new ArrayList<>(map.values());
    }
}
```

## Key Takeaways

- Approach → 
	1. Take out string
	2. Char array
	3. Sort array
	4. Convert to string (for Key)
	5. Push all the related element to key