---
Date: 2025-03-17
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/divide-array-into-equal-pairs/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- The elements present in a **pair are equal**.
- so the numbers needs to be even.
- Yes, wording is confusing

> [!info] References
> - [Divide Array Into Equal Pairs - Leetcode 2206 - Python - YouTube](https://youtu.be/vxcpdClAktE)
### Optimized Solution
```java title="Frequency array"
class Solution {
    public boolean divideArray(int[] nums) {
        int[] bitmap = new int[501];
        for(int i : nums) bitmap[i]++;
        for (int i : bitmap) if(i % 2 != 0) return false;
        return true;
    }
}
```
### Follow Up Solution
using [[BitSet]] 
```java title="Bitset Solution"
public class Solution {
    public boolean divideArray(int[] nums) {
	    // Constraint (1 <= n <= 500)
        BitSet m = new BitSet(501);
        int n = a.length;
        for (int i = 0; i < n; ++i)
            m.flip(nums[i]);
        return m.isEmpty();
    }
}
```
### Initial Solution
```java title="HashSet Solution"
class Solution {
    public boolean divideArray(int[] nums) {
		if(nums.length%2 != 0) return false;
        
        HashSet<Integer> set = new HashSet<>();
        for (int i : nums)
            if(set.contains(i)) set.remove(i);
            else set.add(i); 
        return set.isEmpty();
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 