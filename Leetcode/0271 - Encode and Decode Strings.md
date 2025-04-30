---
Date: 2025-02-18
tags:
  - Leetcode
  - java
  - data_structure
URL: (https://neetcode.io/problems/string-encode-and-decode
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition

> [!info] References
> - 
> - 
### Optimized Solution
```java title="supports word length greater than 9+"
class Solution {
    public String encode(List<String> strs) {
        StringBuilder sb = new StringBuilder();
        for (String s : strs){
            sb.append(s.length()).append("#").append(s);
        }
        return sb.toString();
    }

    public List<String> decode(String str) {
        ArrayList<String> res =  new ArrayList<>();
        int n = str.length();
        int i = 0;
        while(i < n){
            int j = i;
            while(str.charAt(j)!='#')
                j++;        // getting the size of the encoded length
            
            // length of the current word
            int len = Integer.parseInt(str.substring(i,j));
            i = j + 1;      // Moves to the first char of the word
            j = i + len;    // Moves to the last char of the word
            res.add(str.substring(i,j));
            i = j;
        } 
        return res;
    }
}
```
### Follow Up Solution
```java

```
### Initial Solution
```java fold title=" ⭕ Not working - StringIndexOutOfBoundsException"
// The encoding method is correct
// the decoding method is the issue
// it doesn't account for the end of input 
// & if the size of the word is in 2 digits 

class Solution {
    public String encode(List<String> strs) {
        StringBuilder sb = new StringBuilder();
        for (String s : strs){
            sb.append(s.length()).append("#").append(s);
        }
        return sb.toString();
    }

    public List<String> decode(String str) {
        ArrayList<String> res =  new ArrayList<>();
        int n = str.length();
        int len = 0;
        for (int i = 0; i< n; i++){
            if(str.charAt(i+1) == '#')
                len = str.charAt(i) - '0';  
            res.add(str.substring(i+2,i+2+len));
            i = i + len + 2;
        } 
        return res;
    }
}
```
### Key Takeaways
- Encoding Strategy `{java} wordLength + '#' + word ...`

*similar to:* 
- 