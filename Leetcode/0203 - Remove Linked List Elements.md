---
date: 2025-03-28
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/remove-linked-list-elements/description/
Hint: Just use 1 pointer, and use .next
Clarity: High
Solution Type:
  - 2 Pointer
Hardness:
  - Easy
cssclasses:
  - programming-notes
---
### Intuition

> [!info] References
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode res = new ListNode(0, head);
        ListNode curr = res;
        while (curr.next != null) {
            if (curr.next.val == val)
                curr.next = curr.next.next;
            else 
                curr = curr.next;
        }
        return res.next;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 