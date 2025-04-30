---
Hardness: Medium
No.: "2661"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/first-completely-painted-row-or-column/description/
Date: 2025-01-20T14:18
Week:
  - 💥Not in Curriculum
Next Review: January 24, 2025
---

## Useful Video Resources

- [First Completely Painted Row or Column - Leetcode 2661 - Python - YouTube](https://youtu.be/Xhqo5_SPJa8)

## Intuition

- Keep the `mat[][]` in hashmap
- When painting, if you find `mat.length`
- Elements with the same x or y
- You have a complete row/column  
## Optimized Solution

```Java
class Solution {
    public int firstCompleteIndex(int[] arr, int[][] mat) {

        int m = mat.length;
        int n = mat[0].length;

        // using cordinate array to store X & Y of every position of mat
        int[][] cords = new int[m*n+1][2];

        for (int i = 0; i< m; i++)
            for(int j = 0; j < n; j++)
                cords[mat[i][j]] = new int[]{i,j};

        // row & coloum frequency 
        int[] rf = new int[m];
        int[] cf = new int[n];

        for(int i = 0; i < arr.length; i++){
            int[] curr = cords[arr[i]];
            rf[curr[0]]++;
            cf[curr[1]]++;
            // if we complete a row / coloum 
            if (rf[curr[0]] == n || cf[curr[1]] == m)
                return i;
            
        }
        return -1;
    }
}
```

## Initial Solution

```Java
class Solution {
    public int firstCompleteIndex(int[] arr, int[][] mat) {

        int m = mat.length;
        int n = mat[0].length;

        // Storing all the cordinates in hashmap 
        HashMap <Integer, int[]> map = new HashMap<>();
        for (int  i = 0; i< m; i++){
            for(int j = 0; j < n; j++){
                map.put(mat[i][j], new int[]{i,j});
            }
        }

        // row & coloum frequency 
        int[] rf = new int[m];
        int[] cf = new int[n];
        
        for(int i = 0; i < arr.length; i++){
            int[] curr = map.get(arr[i]);
            rf[curr[0]]++;
            cf[curr[1]]++;
            // if we complete a row / coloum 
            if (rf[curr[0]] == n || cf[curr[1]] == m){
                return i;
            }
        }
        return -1;
    }
}
```

## Key Takeaways

- when storing X & Y coordinates, a `[m*n][2]` array is faster than HashMap