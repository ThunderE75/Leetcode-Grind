---
Hardness: Easy
No.: GFG
URL: https://www.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s4231/0
Date: 2024-12-24T20:38
Week:
  - GFG
Next Review: December 28, 2024
---

## Initial Solution

```Java
class Solution {
    // Function to sort an array of 0s, 1s, and 2s
    public void sort012(int[] arr) {
        // code here
        int c0 = 0;
        int c1 = 0;
        int c2 = 0;
        // HashMap <Integer, Integer> map = new HashMap<>();
        for (int i: arr){
            // map.put(i,(map.getOrDefault(i,0)+1));
            if (i == 0)
                c0++;
            else if (i == 1)
                c1++;
            else 
                c2++;
        }
        for (int i =0; i < arr.length; i++){
            if (c0!=0){
                arr[i] = 0;
                c0--;
            } else if (c1!=0){
                arr[i] = 1;
                c1--;
            } else if (c2!=0){
                arr[i] = 2;
                c2--;
            }
        }
        
    }
}
```