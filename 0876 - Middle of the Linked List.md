---
Hardness: Easy
No.: "876"
Solution Type:
  - 2 Pointer
Que Type:
  - Linked List
Clarity: High
URL: https://leetcode.com/problems/middle-of-the-linked-list/description/
Date: 2024-11-16T19:56
Week:
  - Week 3
Next Review: November 20, 2024
---
## Thought Process
- Use [[Floyd’s Cycle-Finding Algorithm]]
- **Two points, one going twice the speed of the other.**

## Useful Video Resources

## Optimized Solution

```Java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

## Follow Up Solution

## Initial Solution [Overcomplicated]

```Java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        int length = 0;
        // while (fast!=null){
        while (true){
            if (fast == null )
                if (length % 2 != 0)
                    return slow;
                else 
                    return slow.next;

            else{
                length++;
                slow = (fast.next==null)?slow.next:slow;
                fast = (fast.next==null)?fast.next:fast;
            }
        }
    }
}
```

## Key Takeaways