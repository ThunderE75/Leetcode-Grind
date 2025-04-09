---
date: 2025-03-26
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/linked-list-cycle-ii/description/
Hint: 
Clarity: High
Solution Type:
  - 2 Pointer
Hardness:
  - Medium
cssclasses:
  - programming-notes
---
### Intuition
- We can use [[Hash Set]] or [[Floyd’s Cycle-Finding Algorithm]]
- See the video 1 for a better understanding of the logic

> [!info] References
> 1. [Coding Ninja - Linked List Cycle II - LeetCode 142 - 3 solutions - Python, JavaScript, Java, C++ - YouTube](https://youtu.be/wzoNwa0eOm0)
### Optimized Solution
```java

```
### Follow Up Solution
```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            // Case 1a: Fast & Slow meet, Cycle was found
            if (fast == slow)
                break;
        }

        // Case 2: Fast reached the end, but no cycle was found
        if (fast == null || fast.next == null)
            return null;

        // Case 1b: Resetting the pointer at start to reach start of cycle
        fast = head;
        while (fast != slow) {
            slow = slow.next;
            fast = fast.next;
        }
        return slow;
    }
}
```
### Initial Solution
```java title="HashSet Solution"
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode curr = head;
        HashSet<ListNode> seen = new HashSet<>();
        while(curr!=null){
            if(seen.contains(curr))
                return curr;
            seen.add(curr);
            curr = curr.next;
        }
        return null;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- [[0141 - Linked List Cycle]]
- [[0287 - Find the Duplicate Number]] 