---
Hardness: Easy
No.: GFG
URL: https://www.geeksforgeeks.org/problems/remove-duplicate-elements-from-sorted-array/0
Date: 2024-12-24T20:37
Week:
  - GFG
Next Review: December 28, 2024
---
## Initial Solution

```Java
class Solution {
    // Function to remove duplicates from the given array
    public int removeDuplicates(int[] arr) {
        // Code Here
        if (arr.length == 0) return 0;
        int idx = 1;
        for (int i = 1 ; i < arr.length; i++){
            if(arr[i] != arr[i-1]){
                arr[idx] = arr[i];
                idx++;
            }
        }
        return idx;
    }
}
```