---
Date: 2025-02-26
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/daily-temperatures/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- An Easy $O(n^2)$ solution is 2 pointer solution using the original array.
- Hint - Use a monotonic decreasing stack

> [!info] References
> - [Daily Temperatures - Monotonic Stack - Leetcode 739 - Python - YouTube](https://youtu.be/cTBiBSnjO3c)
> - This Question is an example of Monotonic Decreasing Stack
### Optimized Solution

[DP Solution - Leetcode](https://leetcode.com/problems/daily-temperatures/solutions/4654558/fastest-solution-beats-100-dp-solution)
The solution works by processing the days from last to first and using already-computed answers to "jump" ahead:

> [!info]- Dynamic Approach More info
> - **Reverse Traversal:** Iterate from the last day backward so that future information is already available.
> - **Hottest Check:** If the current temperature is at least as high as the hottest seen so far, update the hottest and move on (since no warmer day exists).
> - **Jumping Strategy:**
>     - Start by checking the very next day.
>     - If that day isn’t warmer, use the precomputed answer to jump ahead, effectively skipping days that aren’t warmer.
>     - Continue until a warmer day is found.
> - **Store the Result:** Record the number of days jumped as the answer for the current day.

```java fold title="Dynamic Programing Approach"
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int n = temperatures.length;
        int hottest = 0;
        int[] answer = new int[n];
        for (int currDay = n - 1; currDay >= 0; currDay--) {
            int currentTemp = temperatures[currDay];
            // hottest temp seen so far moving from the right
            if (currentTemp >= hottest) {
                hottest = currentTemp;
                continue;
            }
            int days = 1;
            while (temperatures[currDay + days] <= currentTemp) {
                // Use information from answer to search for the next warmer day
                days += answer[currDay + days];
            }
            answer[currDay] = days;
        }
        return answer;
    }
}
```
### Follow Up Solution
```java title="using a pair as the stack type"
// Store both index and temp as int pairs
class Solution {
    public int[] dailyTemperatures(int[] temp) {
        int n = temp.length;
        int[] res = new int[n];
        Stack<int[]> stk = new Stack<>(); // pair: [temp, index]
        for (int i = 0; i < n; i++) {
            int curr = temp[i];
            while (!stk.isEmpty() && curr > stk.peek()[0]) {
                int[] prev = stk.pop();
                res[prev[1]] = i - prev[1];
            }
            stk.push(new int[] {curr, i});
        }
        return res;
    }
}
```
### Initial Solution
```java fold title="Storing the index in stack"
class Solution {
    public int[] dailyTemperatures(int[] temp) {
        int n = temp.length;
        int[] res = new int[n];
        Stack<Integer> stk = new Stack<>();
        for (int i = 0; i < n; i++) {
            if (stk.isEmpty())
                stk.push(i);
            else {
                while (!stk.isEmpty() && temp[stk.peek()] < temp[i]) {
                    int prevIndex = stk.pop();
                    res[prevIndex] = i - prevIndex;
                }
                stk.push(i);
            }
        }
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 