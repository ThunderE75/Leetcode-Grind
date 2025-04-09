---
Hardness: Medium
No.: "973"
Solution Type:
  - Dynamic Programing
Que Type:
  - Priority Queue
Clarity: Medium
URL: https://leetcode.com/problems/k-closest-points-to-origin/description/
Date: 2025-01-04T15:34
Week:
  - Week 4
Next Review: January 8, 2025
---
## Useful Video Resources

- [K Closest Points to Origin - Heap / Priority Queue - Leetcode 973 - Python - YouTube](https://youtu.be/rI2EBUEMfTk)
- [K Closest Points to Origin - YouTube](https://youtu.be/1rEUgAG7f_c)
- [Leetcode 973 - K Closest Points To Origin (JAVA Solution Explained!) - YouTube](https://youtu.be/RnDAeVhnEjI)

> **Guided Steps** (Min Heap)
> 
> ==**TC →**== ==$O(log~n)$==
> 
> - Make a Priority queue with a custom comparator
> - The comparator will calculate squared distance
> - Then add all the coordinates in the queue
> - Create a 2D answer array
> - Poll the queue `k` times
> 
> ---
> - we can get ==$O(log ~k)$== if we use a max heap
> - So, when we reach the queue size of `k`
> - just remove an element
## Optimized Solution

## Follow Up Solution

## Initial Solution

## Key Takeaways