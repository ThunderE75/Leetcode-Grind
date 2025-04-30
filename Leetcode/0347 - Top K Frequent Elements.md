---
Date: 2025-01-31T22:52
Hardness: Medium
No.: "347"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/top-k-frequent-elements/description/
---

## Useful Video Resources
- 
## Copied Solution

```Java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
		
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i : nums)
            map.put(i, map.getOrDefault(i, 0) + 1);
		
        ArrayList<Integer> sorted = new ArrayList<>(map.keySet());
        sorted.sort((a, b) -> map.get(b) - map.get(a));
		
        int[] res = new int[k];
        for(int i=0; i< k; i ++)
            res[i] = sorted.get(i);
		
        return res;
    }
}
```

## Key Takeaways