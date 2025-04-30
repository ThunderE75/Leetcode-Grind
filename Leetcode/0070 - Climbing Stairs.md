---
Hardness: Easy
No.: "70"
Solution Type:
  - Dynamic Programing
Que Type:
  - Dynamic Programing
Clarity: Medium
URL: https://leetcode.com/problems/climbing-stairs/description/
Date: 2024-11-11T00:05
Week:
  - Week 2
Next Review: November 15, 2024
---

## Video Resources

- [Climbing Stairs - Dynamic Programming - Leetcode 70 - Python - YouTube](https://youtu.be/Y0lT9Fck7qI)
- [https://leetcode.com/problems/climbing-stairs/solutions/3708750/4-method-s-beat-s-100-c-java-python-beginner-friendly](https://leetcode.com/problems/climbing-stairs/solutions/3708750/4-method-s-beat-s-100-c-java-python-beginner-friendly) 


> [!important] It’s basically using the Fibonacci sequence

## Assisted Solution

```Java
class Solution {
	public int climbStairs(int n) {
		int[] dp = new int[n + 1];
			dp [0] = 1;
			dp [1] = 1;
			for(int i; i<=n; i++)
				dp[i] = dp[i-1] + dp[i-2];
			return dp[n];
	}
}
```