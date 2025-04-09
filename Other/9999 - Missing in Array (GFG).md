---
Hardness: Easy
No.: GFG
URL: https://www.geeksforgeeks.org/problems/missing-number-in-array1416/0
Date: 2024-12-24T20:35
Week:
  - GFG
Next Review: December 28, 2024
---
## Initial Solution

```Java
class Solution {
    int missingNumber(int arr[]) {
        
        Arrays.sort(arr);
        
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != i + 1) {
                return i + 1;
            }
        }
        return arr.length + 1;
    }
}
```