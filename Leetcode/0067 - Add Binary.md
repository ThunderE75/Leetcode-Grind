---
Hardness: Easy
No.: "67"
Que Type:
  - String
Clarity: Low
URL: https://leetcode.com/problems/add-binary/description/
Date: 2024-11-15T12:55
Week:
  - Week 3
Next Review: November 19, 2024
---
## Useful Resources

- [LeetCode 67. Add Binary Solution Explained - Java - YouTube](https://youtu.be/OEW50g03mT0)
- [Add Binary - Leetcode 67 - Python - YouTube](https://youtu.be/keuWJ47xG8g)
- [String Builder \| Java Placement Course Lecture 13 - YouTube](https://youtu.be/ZLDwskEhIFg)
- [Java \| StringBuilder \| Codecademy](https://www.codecademy.com/resources/docs/java/stringbuilder)
- [StringBuilder in Java with Examples, Methods, and Constructors - Scaler Topics](https://www.scaler.com/topics/java/stringbuilder-in-java/)

## Optimized Solution

```Java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int carry=0;
        int i = a.length()-1;
        int j = b.length()-1;
        while (i >= 0 || j >= 0){
            int sum = carry;
            if (i >= 0) sum += a.charAt(i--) - '0';
            if (j >= 0) sum += b.charAt(j--) - '0';
            
            sb.append(sum%2);
            carry = sum / 2;
        }
        if(carry != 0) sb.append(carry);
        return sb.reverse().toString(); 
    }
}
```

## Key Takeaways

- just use [[String Builder]]
- `sum += a.charAt(i) - '0';`
    - Characters like `'0'` and `'1'` are represented as numbers in ASCII (or Unicode). `'0'` has a numeric value of 48, and `'1'` has a value of 49.
        - `'1' - '0' = 49 - 48 = 1`
        - `'0' - '0' = 48 - 48 = 0`
- `carry = sum / 2`
    - if sum =3 → then carry will be 1

- `carry = sum > 1 ? 1 : 0`
    - Getting carry depend on the quotient we get by dividing sum / 2 that will be our carry. Carry could be either 1 or 0 .
        - if sum is 0 res is 0 & then carry would be 0
        - if sum is 1 res is 1 & carry would be 0
        - if sum is 2 res is 0 & carry would be 1
        - if sum is 3 res is 1 & carry would be 1

## Initial Solution

```Java
???
```