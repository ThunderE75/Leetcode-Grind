---
Date: 2025-02-28
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/generate-parentheses/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- Only add open parenthesis if `open < n`
- Only add closing parenthesis if `closed < open`
- the combo is valid if `Open = closed = n`
- used [[Backtracking]]

> [!info] References
> - [Generate Parentheses - Stack - Leetcode 22 - YouTube](https://youtu.be/s9fokUqJ76A)
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java fold title="Backtracking Solution"
class Solution {
    void backtrack(int open, int closed, int n, List<String> res, StringBuilder sb) {
        if (open == closed && open == n) {
            res.add(sb.toString());
            return;
        }
        // The only condition we are allowed to add open
        if (open < n) {
            sb.append('(');
            backtrack(open + 1, closed, n, res, sb);
            sb.deleteCharAt(sb.length() - 1);
        }
        if (closed < open) {
            sb.append(')');
            backtrack(open, closed + 1, n, res, sb);
            sb.deleteCharAt(sb.length() - 1);
        }
    }

    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        // inital value of open & closed parenthesis count.
        backtrack(0, 0, n, res, sb);
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 