---
Hardness: Medium
No.: "916"
Solution Type:
  - Brute Force
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/word-subsets/description/
Date: 2025-01-10T14:06
Week:
  - 💥Not in Curriculum
Next Review: January 14, 2025
---
## Useful Video Resources

## Optimized Solution

## Follow Up Solution

> [!info] Word Subsets - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/word-subsets/solutions/6257553/simple-max-freq-array-detailed-explanation-solution/?envType=daily-question&envId=2025-01-10](https://leetcode.com/problems/word-subsets/solutions/6257553/simple-max-freq-array-detailed-explanation-solution/?envType=daily-question&envId=2025-01-10)  

```Java
class Solution {
    public List<String> wordSubsets(String[] A, String[] B) {
        
        // Counnting 2nd Array
        int[] maxCharFreq = new int[26];
        int[] tempCharFreq = new int[26];
        for(String b : B ){
            Arrays.fill(tempCharFreq, 0);
            for (char c : b.toCharArray())
                tempCharFreq[c - 'a']+=1;
            for (int i = 0; i < 26; i++)
                maxCharFreq[i] = Math.max(maxCharFreq[i], tempCharFreq[i]);
        }

        List<String> result = new ArrayList<>();
        for (String word : A){
            Arrays.fill(tempCharFreq, 0);
            for (char c : word.toCharArray())
                tempCharFreq[c-'a'] +=1;
        
            boolean check = true;
            for (int i = 0 ; i < 26; i++)
                if (maxCharFreq[i] > tempCharFreq[i]) {
                    check = false;
                    break;
                }
            if(check) 
                result.add(word);
        }
        return result;
    }
}
```

## Initial Solution [not working]

```Java
class Solution {
    public List<String> wordSubsets(String[] words1, String[] words2) {
        HashMap<Character, Integer> map = new HashMap<>();
        List<String> res = new ArrayList<>();
        char[] arr1 = new char[words2.length];
        for (int i = 0; i<words2.length; i++ )
            arr1[i] = words2[i].charAt(0);
            
        for (char c : arr1) {
            map.put(c, (map.getOrDefault(c, 0) + 1));
        }
        for (String s : words1) {
            int cMatch = words2.length;
            for (char ch : s.toCharArray()) {
                if (map.containsKey(ch)) // need to check occourance also
                    cMatch -= 1;
            }
            if (cMatch == 0)
                res.add(s);
        }
        return res;
    }
}
```

## Key Takeaways