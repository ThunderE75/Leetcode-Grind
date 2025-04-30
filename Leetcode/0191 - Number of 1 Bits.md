---
Hardness: Easy
No.: "191"
Solution Type:
  - ⚙️ Bit Manipulation
  - ✨ Special
Que Type:
  - Binary
Clarity: Medium
URL: https://leetcode.com/problems/number-of-1-bits/description/
Date: 2024-12-17T17:04
Week:
  - Week 4
Next Review: December 21, 2024
Remarks: "Convert decimal input to binary & count # of 1sFor Bit Man -> Use & 1 and >>>"
---

## Useful Video Resources

## Optimized Solution

```Java
class Solution {
    public int hammingWeight(int n) {
        int count=0;
        while (n != 0) {
            if ((n & 1) == 1)
                count++;
            n = n >>> 1;
        }
        return count;
    }
}
```

### Working

> The `while` loop runs as long as `n` is not `0`. During each iteration:
> 
> - The least significant bit (LSB) of `n` is checked using `(n & 1)`.
>     - If the LSB is `1`, `count` is incremented.
>     - The number `n` is then **right-shifted** using `>>> 1` to process the next bit.
>         - The unsigned right shift (`>>>`) ensures that zeroes are added on the left side, which works for both positive and negative numbers.
> 
---
> 
> For `n = 11` (binary: `1011`):
> 
> - Step 1: `1011 & 1 → 1` → `count = 1`, shift `n → 0101`
> - Step 2: `0101 & 1 → 1` → `count = 2`, shift `n → 0010`
> - Step 3: `0010 & 1 → 0` → `count = 2`, shift `n → 0001`
> - Step 4: `0001 & 1 → 1` → `count = 3`, shift `n → 0000` (end loop).

## Follow Up Solution

## Initial Solution

```Java
class Solution {
    public int hammingWeight(int n) {
        StringBuilder sb = new StringBuilder();
        int count=0;
        while (n>0){
            sb.append(n % 2);
            n/=2;
        } 
        // SB is the binary input string, but in reverse order
        // but since we are just counting the 1 bits, it doesn't matter
        for (char c : sb.toString().toCharArray()){
            if (c == '1') 
                count+=1;
        }
        return count;
    }
}
```

## Key Takeaways