---
date: 2025-03-28
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/
Hint: 
Clarity: 
Solution Type: 
Hardness:
  - Medium
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- The hints are terrible, but i'll implement it anyways
- i think we need some basic pointers
	- one to tract the 1st swap location
	- Then 2 pointer to have a fixed window that is equal to k, and move it till the right pointer reaches the end
	- then we can swap the ~~nodes~~ *values* around.
## Solution
```java title="Initial Attempt"
class Solution {
    public ListNode swapNodes(ListNode head, int k) {
        ListNode swap1 = head;
        ListNode swap2 = head;

        // finding first location
        for (int i = 0; i < k - 1; i++)
            swap1 = swap1.next;

        ListNode slow = head;
        ListNode fast = swap1;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next;
        }
        swap2 = slow;
        ListNode temp1 = (swap1.next != null) ? swap1.next.next : null;
        ListNode temp2 = (swap2.next != null) ? swap2.next.next : null;

        int val = swap1.val;
        swap1.val = swap2.val;
        swap2.val = val;
        return head;
    }
}
```

```java fold title="The hinted approach"
class Solution {
    public ListNode swapNodes(ListNode head, int k) {
        ListNode curr = head;
        // ListNode curr = new ListNode(0,head);
        ArrayList<Integer> arr = new ArrayList<>();
        while (curr!=null){
            arr.add(curr.val);
            curr = curr.next;
        }

        int temp = arr.get(k - 1);
        arr.set(k - 1, arr.get(arr.size() - k));
        arr.set(arr.size() - k, temp);

        ListNode res = new ListNode(0);
        curr = res;
        for(int i : arr){
            curr.next = new ListNode(i);
            curr = curr.next;
        }
        return res.next;
    }
}
```
## Key Takeaways
- 

> [!info] References
> 1. 

*similar to:* 
- [[0019 - Remove Nth Node From End of List]]