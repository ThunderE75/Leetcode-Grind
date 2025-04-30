---
Hardness: Easy
No.: "232"
Solution Type:
  - 🧠 Design
Que Type:
  - Queue
  - Stacks
  - 🧠 Design
Clarity: Low
URL: https://leetcode.com/problems/implement-queue-using-stacks/description/
Date: 2024-11-14T20:43
Week:
  - Week 2
Next Review: November 18, 2024
cssclasses:
  - programming-notes
---

## Useful Video Resources

- [Implement Queue using Stacks - Leetcode 232 - Python - YouTube](https://youtu.be/eanwa3ht3YQ)

## Optimized Solution

[https://leetcode.com/problems/implement-queue-using-stacks/solutions/64206/short-o-1-amortized-c-java-ruby](https://leetcode.com/problems/implement-queue-using-stacks/solutions/64206/short-o-1-amortized-c-java-ruby)

```Java
class MyQueue {

    Stack<Integer> s1 = new Stack();
    Stack<Integer> s2 = new Stack();

    public MyQueue() {
        
    }
    
    public void push(int x) {
        s1.push(x);
    }
    
    public int pop() {
        peek();
        return s2.pop();
    }
    
    public int peek() {
        if (s2.empty())
            while(!s1.empty())
                s2.push(s1.pop());
        return s2.peek();
    }
    
    public boolean empty() {
        return s1.empty() && s2.empty();
    }
}
```

## Follow Up Solution

- see [[Amortized Analysis]]

- Here, moving all elements from one stack to another may seem costly, but it doesn’t happen every time you do a queue operation.
- Over many queue operations, this transfer step happens only occasionally, so the _average cost per operation_ stays low.
- This is amortized time complexity, where we look at the cost of a whole series of operations rather than just one.

## Key Takeaways

- There will be 2 stacks - $S_1$ & $S_2$
- When `push()` it will always go to $S_1$
- When `pop()` it will always from from $S_2$
- if $S_2$ is empty, move all the elements from $S_1$ to $S_2$ then pop
- `peek()` will return peek from $S_2$
- if both $S_1$ & $S_2$ are empty, return true