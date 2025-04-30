---
Date: 2025-03-27
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/add-two-numbers/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: Medium
cssclasses:
  - programming-notes
---

### Intuition
- if they were of same length, we can just add both nodes, and carry over any excess to the next node.
- but they can of different length, so we will need to traverse both perform the calculation and save to a new list.
- Another approach could be just to extract the number from the list & perform the calculation there, but there will still be Int and Long Overflow (Don't ask me how i know)
- I need to figure out how to handle unequal length lists.

> [!info] References
> - [Explanation on how to handle unequal length list - LeetCode](https://leetcode.com/problems/add-two-numbers/description/comments/1807411/)
> - 
### Optimized Solution
```java

```
### Follow Up Solution
```java title="Iterative Digit-by-Digit Solution"
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode curr = new ListNode();
        ListNode res = curr;
        int carry = 0;
        while (l1 != null || l2 != null || carry > 0) {
            // Addition
            int v1 = (l1 != null) ? l1.val : 0;
            int v2 = (l2 != null) ? l2.val : 0;
            int sum = v1 + v2 + carry;

            carry = sum / 10;
            sum %= 10;

            curr.next = new ListNode(sum);
            curr = curr.next;

            l1 = (l1 == null) ? null : l1.next ;
            l2 = (l2 == null) ? null : l2.next ;
        }
        return res.next;
    }
}
```
### Initial Solution
```java title="Extraction Based approach" error=1
// ⚠️ Does not work due to int/long overflow
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        // we initialize curr as -1 to avoid NullPointerException
        ListNode curr = new ListNode(-1);
        ListNode res = curr;
        long sum = extract(l1) + extract(l2);

        //  sum = 807
        while(sum != 0){
            curr.next = new ListNode((int)sum%10);
            curr = curr.next;
            sum = sum/10;            
        }
        // since we use a dummny -1 node, we need to return next node
        // return res.next;
        return (res.next!=null) ? res.next : new ListNode(0);
    }

    public long extract(ListNode head){
        long res = 0;
        long unit = 1;
        while(head != null){
            res += head.val * unit;
            unit *= 10;
            head = head.next;
        }
        return res;
    }
}
```
### Key Takeaways
- Sometimes doing `sum+=` will increase the time drastically, just initialize new variables. 

*similar to:* 
- [[0067 - Add Binary]]
- 