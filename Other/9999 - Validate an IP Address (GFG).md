---
Hardness: Medium
No.: GFG
URL: https://www.geeksforgeeks.org/problems/validate-an-ip-address-1587115621/1
Date: 2024-12-24T20:32
Week:
  - GFG
Next Review: December 28, 2024
---

## Optimized Solution

```Java
class Solution {

    public boolean isValid(String s) {
        if (s == null || s.length() == 0) return false;
        // Write your code here
        String[] parts = s.split("\\.");
        if(parts.length!=4) return false;
        for(String str : parts){
            if(!isNumeric(str) || str.length()==0 || str.length()>3)
                return false;
            int num = Integer.parseInt(str);
            if (num < 0 || num > 255 ) return false;
            // wtf?
            if (str.length() > 1 && str.charAt(0) == '0') return false;
        }
        return true;
    }
    private boolean isNumeric(String str) {
        for (char c : str.toCharArray()) {
            if (!Character.isDigit(c)) return false;
        }
        return true;
    }
```