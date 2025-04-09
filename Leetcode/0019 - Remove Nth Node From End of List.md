---
date: 2025-03-27
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/
Hint: 
Clarity: 
Solution Type: 
Hardness:
  - Medium
cssclasses:
  - programming-notes
---
### Intuition
- We will have two node, first we made it so that the distance between the fast and slow node is equal to `n`, so basically a [[Sliding Window]] 
- Then we progress both together until fast reaches ends
- We will need a `ListNode` at the head, in case the head is the one being deleted

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode res = new ListNode(0, head);
        ListNode slow = res;
        ListNode fast = head;

        // making the distance fixed
        for (int i = 0; i < n; i++)
            fast = fast.next;
        
        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;
        return res.next;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- [[1721 - Swapping Nodes in a Linked List]]