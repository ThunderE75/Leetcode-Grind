---
date: 2025-02-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/matrix-diagonal-sum/description/
Hint: Try using just one loop
Clarity: High
Solution Type: 
Hardness:
  - Easy
cssclasses:
  - programming-notes
---
# Intuition
- For primary diagonal `i = j`
- for secondary diagonal `i + j = n-1` (n=mat.length)
- if `n is odd`, then the center value `n/2` will be counted twice 
# Optimized Solution

```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int sum = 0;
        int n = mat.length;
        for (int i = 0; i < n; i++) {
            sum += mat[i][i];
            sum += mat[i][n-i-1];
        }
        if (n % 2 != 0)
            sum -= mat[n / 2][n / 2];
        return sum;
    }
}
```
# Initial Solution

```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int sum = 0;
        int n = mat.length;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i == j) sum += mat[i][j];
                if (i + j == n-1) sum += mat[i][j];
            }
        }
        if (n % 2 != 0)
            sum -= mat[n / 2][n / 2];
        return sum;
    }
}
```

*similar to:* 
- [[2133 - Check if Every Row and Column Contains All Numbers]]
- 