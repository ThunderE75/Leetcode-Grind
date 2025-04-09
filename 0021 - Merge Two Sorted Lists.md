---
date: 2024-11-02
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/merge-two-sorted-lists/description/
Hint: 
Clarity: Medium
Solution Type:
  - Brute Force
  - Recursion
Hardness:
  - Easy
cssclasses:
  - programming-notes
---
### Intuition
- 
> [!info] References
> - [Merge Two Sorted Lists - Leetcode 21 - Python - YouTube](https://youtu.be/XIdigk956u0)
### Optimized Solution
```java

```
### Follow Up Solution
```java title="Recursive Solution"
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 == null) return list2;
        if (list2 == null) return list1;
        if (list1.val <= list2.val){
            list1.next =  mergeTwoLists(list1.next, list2);
            return list1;
        } else {
            list2.next =  mergeTwoLists(list1, list2.next);
            return list2;
        }
    }
}
```
### Initial Solution
```java title="Iterative Solution"
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode res = new ListNode();
        ListNode curr = res;
	        /// This needs to be &&
	        while (list1 != null && list2 != null) { 
            if (list1.val < list2.val) {
                curr.next = list1;
                list1 = list1.next;
            } else {
                curr.next = list2;
                list2 = list2.next;
            }
            curr = curr.next;
        }
        curr.next = (list1 != null) ? list1 : list2;
        return res.next;
    }
}
```
### Key Takeaways
- `ListNode head = new ListNode()` → We make a head node, which we will return at the end
- `ListNode current = head` → A current node that at the start points to the head, but will move as we add it
- `while (list1!= null && list2!=null)` → Loop runs until both of lists are full, if with is empty, it exits.
    - We need compare the values in the nodes using `.val` instead of comparing the actual nodes
- Then we add the node that is smaller as the `next node to the current` & move **both** pointers of that list & the current.
- `current.next = (list1 != null) ? list1 : list2` → we add all the remaining nodes from the list that is not empty.
> [!important]
> 
> - `ListNode head = new ListNode()` → We make a node in the linked list using the class provided by the question, instead of the traditional way of using the Linked List syntax.
> - Here we don’t create a new linked list by copying the data from both list into a new list by using the `.add()` method, we just use pointers and `.next()` to point the list that starts with head between both the lists.

*similar to:* 
- [[2570 - Merge Two 2D Arrays by Summing Values]]
- 