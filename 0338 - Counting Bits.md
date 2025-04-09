---
Hardness: Easy
No.: "338"
Clarity: Medium
URL: https://leetcode.com/problems/counting-bits/description/
Date: 2024-11-21T17:48
Week:
  - Week 3
Next Review: November 25, 2024
Remarks: We are given an integer n and need to find all the numbers from 0 to n. For each number, we convert it to its binary representation, count the number of 1s, and store the counts in an array in order.
---
> [!important]
> 
> ## **Rephrased Question**
> 
> ---
> 
> We are given an integer `n` and need to find all the numbers from `0` to `n`. For each number, we convert it to its binary representation, count the number of `1`s, and store the counts in an array in order.

## Useful Video Resources

- [Counting Bits - Dynamic Programming - Leetcode 338 - Python - YouTube](https://youtu.be/RyBM56RIWrM)

## Solution

```Java
class Solution {
    public int[] countBits(int n) {
        int[] arr = new int[n+1];
        for (int i  = 0; i <= n; i++){
            int count = 0;
            int temp = i;
            while (temp > 0){
                count += temp%2;
                temp /= 2;
            }
            arr[i]=count;
        }
        return arr;
    }
}
```

## Key Takeaways

```Java
while (n > 0)
	r += temp%2;
	n /= 2;
```
