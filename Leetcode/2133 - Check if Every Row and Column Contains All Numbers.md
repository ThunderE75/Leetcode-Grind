---
date: 2025-02-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/check-if-every-row-and-column-contains-all-numbers/description/
Hint: 
Clarity: Crystal
Solution Type:
  - Hash Map / Set
Hardness: Easy
cssclasses:
  - programming-notes
---
# Initial Thinking
- 
# Optimized Solution

```java title="Using a single Boolean Array"
class Solution {
    public boolean checkValid(int[][] matrix) {
        int n =  matrix.length;
        boolean[] seen = new boolean[n+1];
        
        // row major wise
        for (int i = 0; i< n; i++){
            Arrays.fill(seen, false);
            for (int j = 0; j< n; j++){
            int curr = matrix[i][j];
                if(seen[curr]) return false;
                seen[curr] = true;
            }
        }
        // column major wise
        for (int i = 0; i< n; i++){
            Arrays.fill(seen, false);
            for (int j = 0; j< n; j++){
                int curr = matrix[j][i];
                if(seen[curr]) return false;
                seen[curr] = true;
            }
        }
        return true;
    }
}
```
# Follow up Solution

```java title="Using a single loop and 2 hash sets"
class Solution {
    public boolean checkValid(int[][] matrix) {
        int n =  matrix.length;
        HashSet<Integer> row = new HashSet<>();
        HashSet<Integer> col = new HashSet<>();
		
        for (int i = 0; i< n; i++){
            row.clear();
            col.clear();
            for (int j = 0; j< n; j++){
                row.add(matrix[i][j]);
                col.add(matrix[j][i]);
            }
            if (row.size()!= n || col.size()!= n ) return false;
        }
        return true;
    }
}
```
# Initial Solution
```java title="Brute Force"
class Solution {
    public boolean checkValid(int[][] matrix) {
        HashSet<Integer> set = new HashSet<>();
		
        // row major wise
        for (int i = 0; i< matrix.length; i++){
            for (int j = 0; j< matrix[0].length; j++){
                set.add(matrix[i][j]);
            }
            if (set.size()!= matrix.length) return false;
            set.clear();
        }
		
        // column major wise
        for (int i = 0; i< matrix.length; i++){
            for (int j = 0; j< matrix[0].length; j++){
                set.add(matrix[j][i]);
            }
            if (set.size()!= matrix.length) return false;
            set.clear();
        }
        return true;
    }
}
```
# Key Takeaways

*similar to:* 
- [[1572 - Matrix Diagonal Sum]]
- [[0036 - Valid Sudoku]]
- [[2661 - First Completely Painted Row or Column]]
- 