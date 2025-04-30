---
Hardness: Easy
No.: "217"
Solution Type:
  - Hash Map / Set
Que Type:
  - Array
Clarity: High
URL: https://leetcode.com/problems/contains-duplicate/description/
Date: 2024-11-17T14:44
Week:
  - Week 3
  - 🚀 Neetcode
Next Review: November 21, 2024
---

## Thought Process

- Obviously, Hash Table
- And a way to use `Arrays.sort(nums);` and check them

## Useful Video Resources

- [LeetCode Contains Duplicate Solution Explained - Java - YouTube](https://youtu.be/4oZsPXG9B94)

## Optimized Solution

```Java
// Uses HashSets instead of HashMaps
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet <Integer> hs = new HashSet<>();
        for(int i : nums ){
            if (hs.contains(i)) return true;
            hs.add(i);
        }
        return false;
    }
}
```
## Initial Solution

```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i : nums) {
            if (map.containsKey(i)) return true;
            else map.put(i, 1);
        }
        return false;
    }
}
```
## Key Takeaways

- It’s `map.containsKey(i)` rather than `map.exists(i)`
- see [[Hash Map]]