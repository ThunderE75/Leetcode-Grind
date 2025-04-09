---
date: 2025-04-01
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/minimum-window-substring/description/
Hint: 
Clarity: Low
Solution Type:
  - Sliding Window
Hardness:
  - Hard
cssclasses:
  - programming-notes
  - no_url_underline
---
## Intuition
- okay, so [[Sliding Window]] with a hash set for occurrence?
- we can use `.substring()` & `.equals()` for a better TC
- return _the **minimum window**_ _of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. -> means we need the exact same frequency.
- there can be a better string builder approach for returning the res;
- wtf is this retarded ass question 
## Solution
```java title="Initial Attempt" error=1
// Does not work correctly 
class Solution {
    public String minWindow(String s, String t) {
        int m = s.length();
        int n = t.length();
        if (m < n)
            return "";
        int[] search = getFreq(t);
        // int[] freq = new int[26];
        int[] freq = getFreq(s.substring(0, n));

        int minLen=Integer.MAX_VALUE, currLen=0;
        String res="";

        int a = 0, b = n;
        while (b <= m) {

            // if(check(getFreq(s.substring(a,b)),search)){
            if(check(search,freq)){
                currLen = b-a ; // -1 because inclusive
                minLen = Math.min(minLen, currLen);
                res = s.substring(a,b);
                // when we find it satifies the freq
                // we reduce the window size
                freq[s.charAt(a)-'a']--;
                a++;
            }
            freq[s.charAt(b)-'a']++;
            b++;            
        }
        return res;
    }

    // only used for initilazation 
    public static int[] getFreq(String s) {
        int[] res = new int[26];
        for (char c : s.toCharArray())
            res[c - 'a']++;
        return res;
    }

    public static boolean check(int[] f1, int[] f2) {
        // f1 needs to always be the target freq array
        // returns true if both freq are some (ignores 0)
        for (int i = 0; i < 26; i++) {
            if (f1[i] == 0)
                continue;
            if (f1[i] != f2[i])
                return false;
        }
        return true;
    }
}
```

```java fold title=""
class Solution {
    public String minWindow(String s, String t) {
        if (s.length() < t.length()) return "";
        HashMap<Character,Integer> window = new HashMap<>();
        HashMap<Character,Integer> tmap = new HashMap<>();

        for(char c : t.toCharArray())
            tmap.put(c, tmap.getOrDefault(c, 0) + 1);
        
        int a = 0, b = 0;
        int countNeeded = tmap.size(), currCount = 0;
        int minLen = Integer.MAX_VALUE;
        String res="";
        while(b<s.length()){
            char c = s.charAt(b);
            window.put(c, window.getOrDefault( c, 0 ) + 1 );

            if(tmap.containsKey(c) && window.get(c).equals(tmap.get(c)))
                currCount++;
            
            while(countNeeded == currCount){
                if (b-a+1 < minLen) {
                    minLen =  b-a+1;
                    res = s.substring(a, b + 1);
                }
                char left = s.charAt(a);
                window.put(left,window.get(left)-1);

                if(tmap.containsKey(left) && window.get(left) < (tmap.get(left)))
                    currCount--;

                a++;
            }

            b++;
        }
        return res;
    }
}
```
## Key Takeaways
- 

> [!info] References
> 1. [Neetcode - 76. Minimum Window Substring - Python](https://youtu.be/jSto0O4AJbM)

*similar to:* 
- [[0567 - Permutation in String]] 
- 