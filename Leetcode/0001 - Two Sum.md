---
Hardness: Easy
No.: "1"
Solution Type:
  - 2 Pointer
  - Hash Map / Set
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/two-sum/description/
Date: 2024-11-01T14:44
Week:
  - Week 1
  - 🚀 Neetcode
Session 1: Mid
Session 2: High
Next Review: November 25, 2024
SR Notes:
  - "[[1-1]]"
---
# Optimized Solution (HashMap)

[Two Sum - Leetcode 1 - HashMap - Python - YouTube](https://www.youtube.com/watch?v=KLlXCFG5TnA)

```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i = 0; i<nums.length; i++){
            int comp = target-nums[i];
            if(map.containsKey(comp)){
                return new int[] {i, map.get(comp)};
            }
            map.put(nums[i], i);
            }
        return null;
    }
}
```

  

## key Takeaways

- `HashMap<Integer,Integer> map = new HashMap<>()` → We make the value of the array the keys & the index of them the values;
    - Then when we get the complement, we can just search that value as keys
- `int comp = target-nums[i]` → to take complement; so we can search what number is required to add with current `nums[i]` to reach target.
- `if(map.containsKey(comp))` → Checks if the compliment of that number exists, if so, we return the current index & the index of the complement that is stored as the value in the HashMap.
- `map.put(nums[i], i)` → We put the value & it’s index if we didn’t find a complement.

# Initial Solution

```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i = 0; i<nums.length; i++){
            for(int j = nums.length-1; j>i; j--){
                if(nums[i]+nums[j]==target){
                return new int[] { i, j };
	           }}}
        return new int[] {};
}}
```

## Approach

- 2 pointers - one from front, other from back, until they meet in the middle