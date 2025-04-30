---
Hardness: Easy
No.: "20"
Solution Type:
  - Brute Force
Que Type:
  - String
Clarity: Medium
URL: https://leetcode.com/problems/valid-parentheses/
Date: 2024-11-01T14:44
Week:
  - Week 1
Session 1: Low
Session 2: High
Next Review: November 22, 2024
SR Notes:
  - "[[1-20]]"
---

## Intuition 

- Will use stack, but can be optimized by storing as array.
- 5 cases jump into mind 
	- `False` - Closing when stack empty
	- `False` - Closing when peek() mismatch
	- `Continue` - Opening (any time)
	- `Continue` - Pop when match peek()
	- `True` - When stack empty
- Possible Optimization
	- Using arrays
	- returning early if length is odd
	- 
## Initial Solution

```Java title="Basic stack answer"
class Solution {
    public boolean isValid(String s) {
        Stack <Character> stk = new Stack<>();
        for (char c : s.toCharArray()){
            if (stk.empty() && (c == ')' || c == '}' || c == ']'))
                return false;
            if (c == ')' && stk.peek()=='(')
                stk.pop();
            else if (c == '}' && stk.peek() == '{')
                stk.pop();
            else if (c == ']' && stk.peek() == '[')
                stk.pop();
            else stk.push(c);
        }
        return stk.empty();
    }
}
```

> [!important] Some people use HashMaps, but i find it pretty useless tbh, and when using those, we also need to use stacks, so why even use it ??

## Key Takeaways

- `if (s.length() % 2 != 0 ) return false` → If it’s not even, then its invalid.
- `if (stk.empty() && (c == ')' || c == '}' || c == ']'))` → if the bracket is closing & the stack is empty, then the input is invalid.
- `if (c == ')' && stk.peek() == '(' ) then stk.pop()` → if there is a corresponding bracket in the stack, then pop it.
- `else stk.add(c)` → If the current character is an opening bracket, add it to the stack.
- `return stk.empty()` → If the stack is empty, the the input is valid.

