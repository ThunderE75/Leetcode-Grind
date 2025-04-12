---
date: 2025-04-12
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/count-symmetric-integers/description/
Hint: Convert to string, make sum func., use substring
Clarity: Medium
Solution Type:
  - Brute Force
Hardness:
  - Easy
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- 
## Solution
```java title="Initial Attempt"
class Solution {
    public int countSymmetricIntegers(int low, int high) {
        int count=0;
        for (int i = low; i <= high; i++){
            String s = Integer.toString(i);
            if (s.length() %2 !=0) 
                continue;
            else {
                int len = s.length()/2;
                if (sum(s.substring(0,len)) == sum(s.substring(len)))
                    count++;
            }
        }
        return count;
    }
    int sum(String s){
        int res = 0;
        for(char c : s.toCharArray())
            res+= c -'0';
        return res;
    }
}
```

```java fold title=""

```
## Key Takeaways
- 

> [!info] References
> 1. 

*similar to:* 
- 