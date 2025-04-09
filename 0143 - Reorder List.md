---
date: 2025-03-28
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/reorder-list/description/
Hint: mid, split, reverse, merge.
Clarity: High
Solution Type:
  - 2 Pointer
Hardness:
  - Medium
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- We do a [[Floyd’s Cycle-Finding Algorithm|Fast & Slow Pointer]] to find the the mid
- Beyond mid, we reverse the list and save the tail of original as the head of 2nd list
- we then traverse both interleafing both of them.
## Solution
```java title="Initial Attempt"
class Solution {
    public void reorderList(ListNode head) {
        ListNode fast = head.next;
        ListNode slow = head;
        // Part 1 - Finding the center
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Part 2 - Seprating the list into List 1 & 2
        ListNode list1 = head;
        ListNode list2 = reverseList(slow.next);
        slow.next = null; // cutting the list

        // Part 3 - Merginging list 1 and list 2
        ListNode curr = head;
        while (list1 != null && list2 != null) {
            ListNode temp1 = list1.next;
            ListNode temp2 = list2.next;

            list1.next = list2;
            list2.next = temp1;

            list1 = temp1;
            list2 = temp2;
        }
    }

    // from leetcode #0206
    public static ListNode reverseList(ListNode head) {
        ListNode curr = head;
        ListNode prev = null;
        while (curr != null) {
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```

## Key Takeaways
- Damn, i still don't fuckin understand why something like this wouldn't work, the variables names are incorrect rn, but you get the idea.
```java 
curr.next = head;
curr.next.next = head2;
head = (head.next != null) ? head.next : null;
head2 = (head2.next != null) ? head2.next : null;
curr = curr.next.next;
```

> [!info] References
> 1. 

*similar to:* 
- [[0141 - Linked List Cycle]]
- [[0206 - Reverse Linked List]]
- 