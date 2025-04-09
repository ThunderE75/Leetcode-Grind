---
date: 2025-03-01
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/apply-operations-to-an-array/description/?envType=daily-question&envId=2025-03-01
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- Weird Wording
- If `i == i+1` set `i = i*2` & `i+1 = 0`
- Place all the zero at the end.

> [!info] References
> - [Apply Operations to an Array - Leetcode 2460 - Python - YouTube](https://youtu.be/ur0srHvM1cA)
### Optimized Solution
```java
class Solution {
    public int[] applyOperations(int[] nums) {
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            if (nums[i] == nums[i + 1]) {
                nums[i] = nums[i] * 2;
                nums[i + 1] = 0;
            }
        }
        // counting swaps
        int j = 0;
        for (int i = 0; i < n; i++) {
            if (nums[i] != 0) {
                nums[j] = nums[i];
                j++;
            }
        }
        Arrays.fill(nums, j, n, 0);
        return nums;
    }
}
```
### Follow Up Solution
```java

```
### Initial Solution
```java
class Solution {
    public int[] applyOperations(int[] nums) {
        int n = nums.length;
        for(int i = 0; i< n-1; i++){
            if (nums[i]==nums[i+1]){
                nums[i] = nums[i]*2;
                nums[i+1] = 0;
            }
        }
        for(int i = 0; i< n-1; i++){
            for(int j = i+1;j < n; j++ ){
                if(nums[i] == 0 && nums[j] != 0){
                    int temp = nums[i];
                    nums[i] = nums[j];
                    nums[j] = temp;
                }
            }
        }
        return nums;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 