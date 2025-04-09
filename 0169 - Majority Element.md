---
Hardness: Easy
No.: "169"
Solution Type:
  - Hash Map / Set
  - ✨ Special
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/majority-element/description/
Date: 2024-11-13T20:21
Week:
  - Week 2
Next Review: November 17, 2024
---
## Video Resources
[Majority Element - Leetcode 169 - Python - YouTube](https://youtu.be/7pnhv842keE)
## Follow Up Solution

using [[Boyer-Moore Voting Algorithm]]

```Java title="Boyer-Moore Voting Algorithm"
class Solution {
    public int majorityElement(int[] nums) {
        int count=0;
        int higest=nums[0];
        for(int i : nums){
            if(count == 0)
                higest = i;
            count += (higest == i) ? 1 : -1; 
        }
        return higest;
    }
}
```

## Initial Solution

```Java
class Solution {
    public int majorityElement(int[] nums) {
        int higest=nums[0];
        HashMap<Integer, Integer> map = new HashMap<>();
		
        // counting the occourence
        for (int i : nums) {
            map.put(i, map.getOrDefault(i, 0) + 1);
            if(map.get(higest) < map.get(i))
                higest = i;
        }
        return higest;
    }
}
```

