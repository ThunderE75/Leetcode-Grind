---
Hardness: Medium
No.: "150"
Solution Type:
  - Just Basics
Que Type:
  - Stacks
Clarity: High
URL: https://leetcode.com/problems/evaluate-reverse-polish-notation/description/
Date: 2025-01-14T19:00
Week:
  - 💥Not in Curriculum
Next Review: January 18, 2025
---
## Initial Solution

```Java
class Solution {
    public int evalRPN(String[] tokens) {
        int res, a, b;
        Stack<String> stk = new Stack<>();
        for (String s : tokens) {
            if (s.equals("+") || s.equals("-") || s.equals("*") || s.equals("/")) {
                b = Integer.parseInt(stk.pop());
                a = Integer.parseInt(stk.pop());
                switch (s) {
                    case "+":
                        stk.push(Integer.toString(a + b));
                        break;
                    case "-":
                        stk.push(Integer.toString(a - b));
                        break;
                    case "*":
                        stk.push(Integer.toString(a * b));
                        break;
                    case "/":
                        stk.push(Integer.toString(a / b));
                        break;
                }
            } else
                stk.push(s);
			
        }
        return Integer.parseInt(stk.pop());
    }
}
```

## Key Takeaways

- Further optimization, instead of using a stack, just use a an array and a pointer yo the last pushed index