---
date: 2025-03-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/search-a-2d-matrix/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- We can brute force but it will be $O(n*m)$, so that's not optimal
- we can first binary search the last index of each to find in witch row it's suppose to exist, and then find it there. The time complexity is $O(log(n * m ))$ 

> [!info] References
> - Flat Array Technique [Nick White - LeetCode 0074 - Java - YouTube](https://youtu.be/eT0UqrYuqbg)
> - 2x Binary Search [Neetcode - Search a 2D Matrix - Leetcode 74 - YouTube](https://www.youtube.com/watch?v=Ber2pi2C0j0)
### Optimized Solution
```java fold title="Flat Array Binary Search"
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0 ;
        int right = m*n-1;

        while(left <= right){
            int mid = left + (right-left)/2;
            int mid_ele = matrix[mid/n][mid%n];
            if(mid_ele == target)
                return true;
            else if (target < mid_ele)
                right = mid-1;
            else 
                left = mid+1;
        }
        return false;
    }
}
```
### Follow Up Solution
```java fold title="Staircase Technique"
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;
        int row = 0 ;
        int col = n-1;

		// Starting from top right
        while(row<m && col >= 0){
            int curr = matrix[row][col];
            if(target < curr)
                col--;
            else if(target > curr)
                row++;
            else 
                return true;
        }
        return false;
    }
}
```
### Initial Solution
```java title="Double Binary Search"
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int n = matrix.length;
        int m = matrix[0].length;
        int left = 0, mid = 0, right = n-1;
        int fRow = 0;

        // To find the target row (mid)
        while (left <= right) {
            mid = left + (right - left) / 2;
            if (matrix[mid][0] <= target && matrix[mid][m-1] >= target){
                fRow = mid; // final target row
                break;
            }
            if (matrix[mid][0] > target)
                right = mid - 1;
            else if (matrix[mid][m-1] < target)
                left = mid + 1;
        }
        
        left = 0;
        mid = 0;
        right = m-1;

        // search the taget row
        while (left <= right) {
            mid = left + (right - left) / 2;
            if (matrix[fRow][mid] == target)
                return true;
            if (matrix[fRow][mid] > target)
                right = mid - 1;
            else
                left = mid + 1;
        }
        return false;
    }
}
```
### Key Takeaways
- The way to achieve flat array is to calculate the mid element `{java}int mid_ele = matrix[mid/n][mid%n];` 

*similar to:* 
- 