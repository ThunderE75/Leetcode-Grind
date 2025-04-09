---
date: 2024-11-02
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
Hint: 
Clarity: Low
Solution Type:
  - Sliding Window
Hardness:
  - Easy
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- What the fuck ?
- Using a [[Sliding Window]] approach 
	- one for buying (a) and other for selling (b)
	- when `{java}b > a` then we calculate, compare & save the price
	- otherwise, we set the buying (a) point to the selling (b) point
	- in any case, we move the selling (b) pointer forward.
- There is a memoization / DP approach to solve this, i am not skilled enough to understand it rn.
## Solution
```java title="Initial Attempt"
class Solution {
    public int maxProfit(int[] prices) {
        int a = 0; // the buy
        int b = 1; // the sell
        int maxProfit = 0;
        while (b < prices.length) { // when selling > buying
            if (prices[a] < prices[b]) {
                int currProfit = prices[b] - prices[a];
                maxProfit = Math.max(currProfit, maxProfit);
            } else   // when buying > selling
                a = b;
            b++;
        }
        return maxProfit;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. [Neetcode - 121. Sliding Window: Best Time to Buy and Sell Stock](https://youtu.be/1pkOgXD63yU)
> 2. [Nick White - LeetCode Best Time to Buy and Sell Stock Solution Explained - Java](https://youtu.be/3RHCb8LY-X4)

*similar to:* 
- 