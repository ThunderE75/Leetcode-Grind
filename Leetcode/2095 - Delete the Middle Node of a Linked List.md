---
Date: 2025-03-28
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/
Hint: 
Clarity: High
Solution Type:
  - 2 Pointer
Hardness: Medium
cssclasses:
  - programming-notes
---

### Intuition
- use [[Floyd’s Cycle-Finding Algorithm|Fast & Slow Pointer]] and just delete the middle node
- 

> [!info] References
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java title="without the use of a prev pointer"
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if (head.next == null) return null;
        ListNode slow = head;
        ListNode fast = head.next.next;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        slow.next = slow.next.next;
        return head;
    }
}
```
### Initial Solution
```java
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if (head.next == null) return null;
        ListNode prev = head;
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }
            prev.next = slow.next;
        return head;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- [[0876 - Middle of the Linked List]]
- [[0019 - Remove Nth Node From End of List]]
- 