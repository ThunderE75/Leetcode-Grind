---
Hardness: Easy
No.: GFG
URL: https://www.geeksforgeeks.org/problems/move-all-zeroes-to-end-of-array0751/0
Date: 2024-12-24T20:34
Week:
  - GFG
Next Review: December 28, 2024
---

## Initial Solution

```Java
class Solution {
    void pushZerosToEnd(int[] arr) {
        // code here
        int temp;
        int front = 0;
        
        for (int i=0; i< arr.length; i++){
            if(arr[i]!= 0){
                temp = arr[i];
                arr[i] = arr[front] ;
                arr[front] = temp;
                front++;
            }
        }
    }
}
```