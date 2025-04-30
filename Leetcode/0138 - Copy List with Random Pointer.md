---
Date: 2025-03-29
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/copy-list-with-random-pointer/description/
Hint: Traverse, HashMap, Deep Copy via Map get
Clarity: Medium
Solution Type:
  - 2 Pointer
  - Hash Map / Set
Hardness: Medium
cssclasses:
  - programming-notes
  - no_url_underline
---

## Intuition
- What the fuck, i do not understand the question
- 
## Solution
```java title="Initial Attempt"
class Solution {
    public Node copyRandomList(Node head) {
        Node curr = head;
        HashMap<Node, Node> map = new HashMap<>();
        map.put(null,null);
        
        // Step 1 - Traversing the list to create and store nodes
        while(curr != null){
            Node temp = new Node(curr.val);
            map.put(curr,temp);
            curr = curr.next;
        }

        // Step 2 - Linking the nodes
        curr = head;
        while(curr!=null){
            Node temp = map.get(curr);
            temp.next = map.get(curr.next);
            temp.random = map.get(curr.random);
            curr = curr.next;
        }

        return map.get(head);
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Copy List with Random Pointer - Linked List - Leetcode 138](https://youtu.be/5Y2EiZST97Y)
> 2. [0138. Copy List With Random Pointer - Explanation](https://neetcode.io/solutions/copy-list-with-random-pointer)

*similar to:* 
- 