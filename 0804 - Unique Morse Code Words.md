---
Hardness: Easy
No.: "804"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: Crystal
URL: https://leetcode.com/problems/unique-morse-code-words/description/
Date: 2025-01-13T23:04
Week:
  - 💥Not in Curriculum
---
## Initial Solution

```Java
class Solution {
    public int uniqueMorseRepresentations(String[] words) {
        HashSet<String> unique = new HashSet<>();
        String[] lookup = { 
            ".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."
         };

        int count = 0;
        StringBuilder sb = new StringBuilder();
        for (String word : words) {
            for (char c : word.toCharArray()) {
                sb.append(lookup[c - 'a']);
            }
            if (!unique.contains(sb.toString())) {
                unique.add(sb.toString());
                count += 1;
            }
            sb.delete(0, sb.length());
        }
        return count;
    }
}
```