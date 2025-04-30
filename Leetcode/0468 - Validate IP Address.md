---
Hardness: Medium
No.: "468"
Solution Type:
  - ✨ Special
Que Type:
  - String
Clarity: Low
URL: https://leetcode.com/problems/validate-ip-address/description/
Date: 2024-12-24T20:14
Week:
  - 💥Not in Curriculum
Next Review: December 28, 2024
---

## Useful Video Resources

## Key Takeaways

- For `IPv4` contains 4 bytes separated via `.`
    - Each segment will be between 0 & 255
    - Leading Zeros are **not allowed**
- For `IPv6` contains 8 bytes separated via `:`
    - Each segment is a hexadecimal number (not case sensitive)
    - Leading Zeros **are allowed**
- Edge Cases
    - Check for leading & trailing `.` & `:`
- ⭐ Useful build-in Methods
    - `.indexOf()` → to check 1st occurrence & returns `-1` if it doesn’t exist.
    - `.startsWith()` & `.endsWith()` → to check for leading & trailing characters
    - `.split(”\\,”)` to split a string into array separated with the delimiter `,`
    - Create 2 custom methods to check if a string is valid number & to check if a string is a valid Hex

## Optimized Solution

```Java
class Solution {
    public String validIPAddress(String queryIP) {
        // Check for IPv4
        if (queryIP.indexOf(":") == -1) {
            if (queryIP.startsWith(",") || queryIP.endsWith("."))
                return "Neither";
            String[] parts = queryIP.split("\\.");
            if (parts.length != 4)
                return "Neither";
			
            for (String part : parts) {
                if (part.length() == 0 || part.length() > 3 || !isNumber(part))
                    return "Neither";
				
                try {
                    int num = Integer.parseInt(part);
                    if (num < 0 || num > 255)
                        return "Neither";
                } catch (NumberFormatException e) {
                    return "Neither";
                }
                if (part.length() > 1 && part.charAt(0) == '0')
                    return "Neither";
            }
            return "IPv4";
        } else {
            if (queryIP.startsWith(":") || queryIP.endsWith(":"))
                return "Neither";
			
            String[] parts = queryIP.split("\\:");
            if (parts.length != 8)
                return "Neither";
			
            for (String part : parts) {
                if (part.length() == 0 || part.length() > 4 || !isHex(part))
                    return "Neither";
            }
            return "IPv6";
        }
    }
	
    boolean isNumber(String s) {
        for (char c : s.toCharArray()) {
            if (!Character.isDigit(c))
                return false;
        }
        return true;
    }

    boolean isHex(String s) {
        for (char c : s.toCharArray()) {
            if (!((c >= '0' && c <= '9') || (c >= 'a' && c <= 'f') || (c >= 'A' && c <= 'F'))) {
                return false;
            }
        }
        return true;
    }
}
```