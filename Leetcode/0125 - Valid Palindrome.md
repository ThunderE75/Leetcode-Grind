---
Hardness: Easy
No.: "125"
Solution Type:
  - 2 Pointer
Que Type:
  - String
Clarity: High
URL: https://leetcode.com/problems/valid-palindrome/description/
Date: 2024-11-04T18:51
Remarks: "to Prevent TLE, save the char in vars, use a single loop "
---

## Intuition 
- We can use 2 Pointer Approach.
- Do not, just store all the values in hashmap and check for odd.
- use [[ASCII Encoding]] 

## Initial Solution

```Java
class Solution {
    public boolean isPalindrome(String s) {
        char l, r;
        for(int i=0, j=s.length()-1; i<=j;){
            l=s.charAt(i);
            r=s.charAt(j);

            if(l<48 || (l>57 && l <65) || (l>90 && l<97) || l>122){
                i++;
                continue;
            }
            if(r<48 || (r>57 && r <65) || (r>90 && r<97) || r>122){
                j--;
                continue;
            }
            i++;
            j--;
            if (Character.toLowerCase(l) != Character.toLowerCase(r)) return false;
        }
        return true;
    }
}
```

```java fold title="Uses an Extra String, but less messy"
class Solution {
    public boolean isPalindrome(String s) {
        String sl = s.toLowerCase();
        for (int left = 0, right = sl.length() - 1; left <= right;) {
            char i = sl.charAt(left);
            char j = sl.charAt(right);
            if ((i < 48) || (i > 57 && i < 97) || (i > 122)) {
                left++;
                continue;
            }
            if ((j < 48) || (j > 57 && j < 97) || (j > 122)) {
                right--;
                continue;
            }
            if (i != j)
                return false;
            left++;
            right--;
        }
        return true;
    }
}
```
## Notes

- Hint [[ASCII Encoding]]

*similar to:* 
- [[]]