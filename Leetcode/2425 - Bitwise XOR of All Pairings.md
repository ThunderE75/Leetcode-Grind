---
Hardness: Medium
No.: "2425"
Solution Type:
  - ⚙️ Bit Manipulation
Que Type:
  - Binary
Clarity: Low
URL: https://leetcode.com/problems/bitwise-xor-of-all-pairings/description/
Date: 2025-01-16T14:00
Week:
  - 💥Not in Curriculum
Next Review: January 20, 2025
---
## Useful Video Resources
- [Bitwise XOR of All Pairings - Leetcode 2425 - Python - YouTube](https://youtu.be/H9zVwDf6Frk)

## Optimized Solution

> [!info] Bitwise XOR of All Pairings - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/bitwise-xor-of-all-pairings/solutions/2646552/java-c-python-easy-and-concise/?envType=daily-question&envId=2025-01-16](https://leetcode.com/problems/bitwise-xor-of-all-pairings/solutions/2646552/java-c-python-easy-and-concise/?envType=daily-question&envId=2025-01-16)  

```Java
    public int xorAllNums(int[] A, int[] B) {
        int x = 0, y = 0;
        for (int a: A)
            x ^= a;
        for (int b: B)
            y ^= b;
        return (A.length % 2 * y) ^ (B.length % 2 * x);
    }
```

## Initial Solution

> [!info] Bitwise XOR of All Pairings - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/bitwise-xor-of-all-pairings/solutions/2646801/java-beats-100-beginner-friendly-with-comments-detail-explaination/?envType=daily-question&envId=2025-01-16](https://leetcode.com/problems/bitwise-xor-of-all-pairings/solutions/2646801/java-beats-100-beginner-friendly-with-comments-detail-explaination/?envType=daily-question&envId=2025-01-16)  

```Java
class Solution {
    public int xorAllNums(int[] nums1, int[] nums2) {
        boolean n1even = (nums1.length % 2 == 0);
        boolean n2even = (nums2.length % 2 == 0);
        if (n1even && n2even)
            return 0;
        else if (!n1even && n2even) {
            int res = 0;
            for (int i : nums2)
                res ^= i;
            return res;
        } else if (n1even && !n2even) {
            int res = 0;
            for (int i : nums1)
                res ^= i;
            return res;
        }

        // when both are odd
        int res = 0;
        for (int i : nums1) {
            for (int j : nums2)
                res ^= i ^ j;
        }
        return res;

    }
}
```

## Key Takeaways

1. XOR Properties
    - $X \oplus X = 0$
    - $X \oplus ~ 0 = 0$
    - $X \oplus X \oplus X \oplus \cdots ~n^{times}$
        - (because $x \oplus x$ cancels out)
        - $0$ if $n$ is even
        - $x$ if $n$ is odd
2. **Different cases in this program**
    
    **Case 1 -** Both `arr1` & `arr2` are of even length → return 0;
    
    **Case 2 -** Both `arr1` & `arr2` are of odd length →
    
    > XOR every permutation of `arr1` & `arr2`
    
    **Case 3 -** `arr1` is odd `arr2` is of even length →
    
    > XOR every element of `arr2` because when we XOR each permutation, the elements of `arr1` appear twice, so they cancel out. [==[Bitwise XOR of All Pairings - Leetcode 2425 - Python - YouTube](https://youtu.be/H9zVwDf6Frk?t=442)==]
    
    **Case 4 -** `arr1` is even `arr2` is of odd length →
    
    > Vice versa of Case 3  
    > XOR every element of  
    > `arr1` because when we XOR each permutation, the elements of `arr2` appear twice, so they cancel out. [==[Bitwise XOR of All Pairings - Leetcode 2425 - Python - YouTube](https://youtu.be/H9zVwDf6Frk?t=442)==]