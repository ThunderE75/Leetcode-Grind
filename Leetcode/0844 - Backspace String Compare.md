---
Hardness: Easy
No.: "844"
Solution Type:
  - 2 Pointer
  - Stack
  - String Builder
Que Type:
  - String
Clarity: Low
URL: https://leetcode.com/problems/backspace-string-compare/description/
Date: 2024-11-20T13:28
Week:
  - Week 3
Next Review: November 24, 2024
---
## Thought Process

- Use Stacks ( 2?)
- What if we find # for an empty stack ?
- Used StringBuilder

- `StringBuilder sb = new StringBuilder();`
    - Has almost all the string class
    - use `.append()` to add stuff at the end
    - use `.deleteCharAt()` to remove
    - use `.reverse()` to reverse it
    - use `.toString()` to convert StringBuilder into a string

## Useful Video Resources

> [!important] I didn’t use any solution used in the video

- [https://youtu.be/vgog1EuEJYQ](https://youtu.be/vgog1EuEJYQ)
- [https://youtu.be/k2qrymM_DOo](https://youtu.be/k2qrymM_DOo)

## Optimized Solution

```Java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        return build(s).equals(build(t));
    }
    public String build(String str){
        StringBuilder sb = new StringBuilder();
        for (char c : str.toCharArray() ){
            if (c == '#') {
                if (sb.length() > 0)
                    sb.deleteCharAt(sb.length() - 1);
            } else
                sb.append(c);
        }
        return sb.toString(); 
    }
}
```

## Follow Up Solution

## Initial Solution

```Java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        StringBuilder s1 = new StringBuilder(s.length());
        StringBuilder s2 = new StringBuilder(t.length());

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '#') {
                if (s1.length() > 0)
                    s1.deleteCharAt(s1.length() - 1);
            } else
                s1.append(s.charAt(i));
        }
        for (int i = 0; i < t.length(); i++) {
            if (t.charAt(i) == '#') {
                if (s2.length() > 0)
                    s2.deleteCharAt(s2.length() - 1);
            } else
                s2.append(t.charAt(i));
        }
        return s1.toString().equals(s2.toString());
    }
}
```

```Java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        Stack<Character> stk1 = new Stack<>();
        Stack<Character> stk2 = new Stack<>();

        for (char c : s.toCharArray() ){
            if (c == '#' && !stk1.isEmpty()) 
                stk1.pop();
            else 
                stk1.push(c);
        }
        for (char c : t.toCharArray() ){
            if (c == '#' && !stk2.isEmpty()) 
                stk2.pop();
            else 
                stk2.push(c);
        }

        while (!stk1.isEmpty() && !stk2.isEmpty()) {
            if (stk1.pop() != stk2.pop())
                return false;
        }
        return stk1.isEmpty() && stk2.isEmpty();
    }
}
```

## Key Takeaways