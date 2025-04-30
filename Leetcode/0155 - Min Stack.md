---
Date: 2025-03-01
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/min-stack/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- Don't over think it, you don't need to implement stack from scratch.
- you just need to add a 'feature' that return the min value of the stack in $O(1)$ time.

> [!info] References
> - [# Min Stack - Explanation](https://neetcode.io/solutions/min-stack)

### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java title="Double Stack Method"
class MinStack {
    Stack <Integer> stk;
    Stack <Integer> minStk;
    public MinStack() {
        stk = new Stack<>();
        minStk = new Stack<>();
    }
    
    public void push(int val) {
        stk.push(val);
        // remember to also push if >=
        if(minStk.isEmpty() || minStk.peek() >= val )
            minStk.push(val);        
    }
    
    public void pop() {
        int temp = stk.pop();
        if (minStk.peek() == temp)
            minStk.pop();
    }
    
    public int top() {
        return stk.peek();
    }
    
    public int getMin() {
        return minStk.peek();
    }
}

```
### Key Takeaways
- 

*similar to:* 
- 