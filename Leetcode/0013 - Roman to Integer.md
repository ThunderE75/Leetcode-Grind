---
Hardness: Easy
No.: "13"
Solution Type:
  - Hash Map / Set
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/roman-to-integer/description/
Date: 2024-11-19T19:25
Week:
  - Week 3
Next Review: November 23, 2024
---

## Useful Video Resources

- Another Approach
    - [Roman to Integer - Leetcode 13 - Python - YouTube](https://youtu.be/3jdxYj3DD98)
    - [Roman to Integer - LeetCode 13 \| Java - YouTube](https://youtu.be/k4KgVd5LQk8)

## Optimized Solution

```Java
// Try to solve using Switch case instead
```

## Follow Up Solution

## Key Takeaways

- `III` can be processes as 1 character, i.e. `1+1+1`
- So, Every roman number is either 1 or 2 character long
- Also, do not forget to check that you are inbounds for strings

  

## Initial Solution

```Java
// Final Solution 
class Solution {
    public int romanToInt(String s) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("I", 1);
        map.put("IV", 4);
        map.put("V", 5);
        map.put("IX", 9);
        map.put("X", 10);
        map.put("XL", 40);
        map.put("L", 50);
        map.put("XC", 90);
        map.put("C", 100);
        map.put("CD", 400);
        map.put("D", 500);
        map.put("CM", 900);
        map.put("M", 1000);
        int total = 0;

        for (int i = 0; i < s.length(); i++) {
            if ((i + 1) < s.length() && map.containsKey(s.substring(i, i + 2))) {
                total += map.get(s.substring(i, i + 2));
                i++;
            } else
                total += map.get(s.substring(i, i + 1));
        }
        return total;
    }
}
```

```Java
class Solution {
    public int romanToInt(String s) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("I", 1);
        map.put("IV", 4);
        map.put("V", 5);
        map.put("IX", 9);
        map.put("X", 10);
        map.put("XL", 40);
        map.put("L", 50);
        map.put("XC", 90);
        map.put("C", 100);
        map.put("CD", 400);
        map.put("D", 500);
        map.put("CM", 900);
        map.put("M", 1000);
        int total=0;

        for(int i=0; i<s.length()-1; i++){
            if (map.containsKey(s.substring(i,i+2))){
                total += map.get(s.substring(i,i+2));
                i++;
            }else 
                total += map.get(s.substring(i,i+1));
                // total += map.get(s.charAt(i));
        }
        return total;
    }
}
```

```Java
class Solution {
    public int romanToInt(String s) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("I", 1);
        map.put("IV", 4);
        map.put("V", 5);
        map.put("IX", 9);
        map.put("X", 10);
        map.put("XL", 40);
        map.put("L", 50);
        map.put("XC", 90);
        map.put("C", 100);
        map.put("CD", 400);
        map.put("D", 500);
        map.put("CM", 900);
        map.put("M", 1000);
        int total = 0;

        for (int i = 0; i < s.length(); i++) {
            if ((i + 3) < s.length() && map.containsKey(s.substring(i, i + 3))) {
                total += map.get(s.substring(i, i + 3));
                i += 2;
            } else if ((i + 2) < s.length() && map.containsKey(s.substring(i, i + 2))) {
                total += map.get(s.substring(i, i + 2));
                i++;
            } else
                total += map.get(s.substring(i, i + 1));
        }
        return total;
    }
}
```