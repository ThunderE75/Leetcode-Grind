---
Hardness: Easy
No.: "206"
Solution Type:
  - 2 Pointer
Que Type:
  - Linked List
Clarity: Low
URL: https://leetcode.com/problems/reverse-linked-list/description/
Date: 2024-11-12T00:12
Week:
  - Week 2
Next Review: November 16, 2024
---

### Intuition
- To Reverse it, we can just traverse through it, and change the the curr.next to previous

> [!info] References
> [LeetCode - Reverse Linked List Solution - YouTube](https://youtu.be/NhapasNIKuQ)
> [Reverse Linked List - Iterative AND Recursive - Leetcode 206 - Python - YouTube](https://youtu.be/G0_I-ZF0S38)
> [Step By Step Visualization - LeetCode Solution](https://leetcode.com/problems/reverse-linked-list/solutions/6550282/0ms-100-step-by-step-visualization-easiest-to-understand-java-c-python)
> 
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java title="Iterative Approach"
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode curr = head;
        ListNode prev = null;
        while(curr != null){
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 






## Useful Videos



```java title="ListNode class"
curr.next = prev;
prev = curr;
curr = next;
```
## Assisted Solution

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        while(head!=null){
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}
```

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        return reverse(head,null);
    }
    public ListNode reverse(ListNode curr, ListNode prev){
        if (curr==null) return prev;
        ListNode next = curr.next;
        curr.next = prev;
        return reverse (next, curr);
    }
}
```
