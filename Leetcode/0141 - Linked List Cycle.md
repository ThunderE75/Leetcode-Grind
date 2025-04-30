---
Hardness: Easy
No.: "141"
Solution Type:
  - 2 Pointer
  - Hash Map / Set
  - Recursion
  - ✨ Special
Que Type:
  - Linked List
Clarity: Medium
URL: https://leetcode.com/problems/linked-list-cycle/description/
Date: 2024-11-07T20:24
Week:
  - Week 2
Next Review: November 11, 2024
---

### Intuition
- just use [[Floyd’s Cycle-Finding Algorithm]]
- 
> [!info] References
> - [Linked List Cycle - Floyd's Tortoise and Hare - Leetcode 141 - Python - YouTube](https://youtu.be/gBTe7lFR3vc)
> - [LeetCode Linked List Cycle Solution Explained - Java - YouTube](https://youtu.be/6OrZ4wAy4uE)
> - [Floyd's cycle detection algorithm (Tortoise and hare) - Inside code - YouTube](https://youtu.be/PvrxZaH_eZ4)
### Optimized Solution
```java fold

```
### Follow Up Solution
```java fold

```
### Initial Solution
```java title="Two Pointer Approach"
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
            if (fast == slow) return true;
        }
        return false;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- [[0142 - Linked List Cycle II]]
- [[0287 - Find the Duplicate Number]] 
