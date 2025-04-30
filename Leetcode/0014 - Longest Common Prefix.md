---
Hardness: Easy
No.: "14"
Solution Type:
  - 🧠 Design
Que Type:
  - String
Clarity: Low
URL: https://leetcode.com/problems/longest-common-prefix/description/
Date: 2024-12-17T17:44
Week:
  - Week 4
Next Review: December 21, 2024
Remarks: either you take 1st as prefix, or add as you check it in every string
---

## Useful Video Resources

- [https://youtu.be/bl8ue-dTxgs](https://youtu.be/bl8ue-dTxgs)
- [https://youtu.be/0sWShKIJoo4](https://youtu.be/0sWShKIJoo4)

## Optimized Solution

```Java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        // if there are no elements in the array
        if (strs.length == 0) return ""; 
        // set prefix as the 1st element
        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++ ){
            // Runs until it finds a prefix that starts at index 0
            while (strs[i].indexOf(prefix) != 0)
                // Removes the last character of the string
                prefix = prefix.substring(0,prefix.length()-1);
        }
        return prefix;
    }
}
```

## Follow Up Solution

## Initial Copied Solution

```Java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        StringBuilder sb = new StringBuilder();
        // We run the loop taking the first element as refrence 
        for (int i = 0; i < strs[0].length(); i++) {
            // Sequentially check each element 
            for (String s : strs) {
                // if the current & 1st char are not same, 
                // or i has exceded the current elements length
                // return string 
                if (i == s.length() || s.charAt(i) != strs[0].charAt(i))
                    return sb.toString();
            }
            // Append the current character in the result 
            // after checking if every element has it
            sb.append(strs[0].charAt(i));
        }
        return sb.toString();
    }

}
```

## Key Takeaways