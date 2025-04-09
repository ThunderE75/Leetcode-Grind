---
date: 2025-03-20
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/koko-eating-bananas/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- How?
- 

> [!info] References
> - [Neetcode - Koko Eating Bananas - Binary Search - Leetcode 875 - Python - YouTube](https://youtu.be/U2SozAs9RzA)
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
    public int minEatingSpeed(int[] piles, int hours) {
        int total = 0;
        int n = piles.length;
        int left = 1;
        int right = Arrays.stream(piles).max().getAsInt();

        while (left <= right) {
            int mid = left + (right - left) / 2;
            long time = 0;

            for (int banana : piles)
                time += (banana - 1) / mid + 1;

            if (time > hours) // if current time is more then guard retrun time
                left = mid + 1;
            else
                right = mid - 1;
        }
        return left;
    }
}
```
### Key Takeaways
- For binary search, you don't need actual array, just lower and upper bounds
- To get the max value in an array `{java}Arrays.stream(arr).max().getAsInt();` 

> [!error]- Explanation for Optimization for lower and upper bound
> 
> `{java}int left = (total - 1) / hours + 1;`
> `{java}int right = (total - n) / (hours - n + 1) + 1;`
> 
> A couple tips/optimizations I noticed:
> 1. We shouldn't start at l = 1. We should start at l = ceil(sum(piles)/h.  Take [3,6,7,11] and h = 8 as an example. Logically, we know that to finish all bananas within 8 hours, the minimum rate is [3 + 6 + 7 + 11] / 8 = 27 / 8 = 3.375. Koko can't eat partial bananas, so round up to 4.
> 2. We don't need to use min() to track the result. We can simply store 'res = k' every time, instead of 'res = min(res, k)'. Think about this logically:
>    
>    a) If we cannot eat all the bananas within H hours at rate K, we increase our L (slow) pointer and do not store a result
>    
>    b)  If we can eat all the bananas within H hours at rate K, we decrease our R (fast) pointer and store a result
>    
>    c) If we hit an exact match (Koko eats all bananas in exactly H hours), we store our result and decrease our R (fast) pointer. Since we have just decreased our fast pointer, there are two options: 
>          Option 1: It is impossible for us to ever eat all bananas within H hours.
>          Option 2: We find a valid rate, but this rate is less than the previous rate we discovered.
> 
> 3. Minor, more obvious point: We cannot break early the first time we eat all bananas in exactly H hours.  Take [3,6,7,11] and h = 8 as an example.  If our rate is 5, we will eat all bananas in 8 hours, but 5 is not the lowest possible rate of consumption.
 
*similar to:* 
- 