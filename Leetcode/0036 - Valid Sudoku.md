---
date: 2025-02-16
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/valid-sudoku/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: Medium
cssclasses:
  - programming-notes
---
# Initial Thinking

- We can easily check the row & column rules, but how to check each chunk ?
- to check chunk (sub-boxes) see [[#Solution]]
- We can hardcode lengths, for better time

> [!faq]- How can we solve it in one pass ?
> Use a Hashset, the key keeps track of coordinate, the value is a hashset of all the numbers in that sub-box
> 
> `{java} Map<String, Set<Character>> squares = new HashMap<>();`
> 
> we will now need to use [[Hash Map#.computeIfAbsent()]]

> [!info] References
> - [Valid Sudoku - Amazon Interview Question - Leetcode 36 - Python - YouTube](https://youtu.be/TjFXEUCMqI8)
> - [Solutions](https://neetcode.io/solutions/valid-sudoku)
# Solution
```java title="Brute Force" info:29-31
class Solution {
    public boolean isValidSudoku(char[][] board) {
        HashSet<Character> set = new HashSet<>();
		
        // row major wise
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                char n = board[i][j];
                if (n == '.') continue;
                if (set.contains(n)) return false;
                set.add(n);
            }
            set.clear();
        }
        set.clear();
        
        // column major wise
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                char n = board[j][i];
                if (n == '.') continue;
                if (set.contains(n)) return false;
                set.add(n);
            }
            set.clear();
        }
        set.clear();
		
        // still need to check for sub-boxes
        // there are a total of 9 sub-boxes 
        // Neetcode's brain child
        for (int square = 0; square < 9; square++) {
            set.clear();
            for (int i = 0; i < 3; i++) {
                for (int j = 0; j < 3; j++) {
					
                    // calculates the actual location of the boxes
                    int row = (square / 3) * 3 + i;
                    int col = (square % 3) * 3 + j;
					
                    // same logic
                    char n = board[row][col];
                    if (n == '.') continue;
                    if (set.contains(n)) return false;
                    set.add(n);
                }
            }
        }
        return true;
    }
}
```
# Key Takeaways

*similar to:* [[2133 - Check if Every Row and Column Contains All Numbers]]