---
Date: 2025-03-01
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- using [[Backtracking]] 

> [!info] References
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java fold title="Backtracking Method"
class Solution {
    List<String> res = new ArrayList<>();
    String[] lookup = {"", "", "abc", "def", "ghi", "jkl", "mno", "qprs", "tuv", "wxyz"};
    public List<String> letterCombinations(String digits) {
        if (digits.isEmpty()) return res;
        backtrack(0,"",digits);
        return res;
    }
    void backtrack(int i, String curr, String digits){
        // base case
        if (curr.length() == digits.length()){
            res.add(curr);
            return;
        }
        // colllection of all possible character that digit can have
        String poss = lookup[digits.charAt(i) - '0'];
        for (char c : poss.toCharArray()){
            backtrack(i+1, curr + c, digits);
        }
    }
}
```
### Key Takeaways
- 

*similar to:* 
- [[0022 - Generate Parentheses]]