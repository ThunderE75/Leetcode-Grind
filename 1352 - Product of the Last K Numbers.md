---
date:
  "{ date:YYYY-MM-DD }": 
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/product-of-the-last-k-numbers/description/
Hint: Prefix-sum, when zero don't multiply, when retrieving don't divide if zero is zero
Clarity: Low
Solution Type:
  - Prefix-sum
Hardness: Medium
cssclasses:
---
# Useful Video Resources
- [Product of the Last K Numbers \| Leetcode 1352 - YouTube](https://youtu.be/rtZt0ApLodo)
# Initial Solution
```java
class ProductOfNumbers {
    ArrayList<Integer> prefix;

    public ProductOfNumbers() {
        prefix = new ArrayList<>();
        prefix.add(1);
    }

    public void add(int num) {
        if (num == 0){
            prefix.clear();
            prefix.add(1);
        } else
            prefix.add(prefix.get(prefix.size() - 1) * num);
    }

    public int getProduct(int k) {
        if (prefix.size() <= k) return 0;
        int len = prefix.size();
        return prefix.get(len-1) / prefix.get(len-k-1);
    }
}
```
# Key Takeaways
- Create an [[Arraylist]] to store the values from the stream.
- We compute the prefix sum array
- To get the product of last *k* numbers, we get the last number from prefix sum arraylist and divide by `(size - k)` 
- Issues that we might encounter
	1. A **zero** in the stream
		- will change all the upcoming data in zero, so we don't multiply the number when adding to prefix array if the `last-1` is a **zero**
	2. Division by **zero**
		- In this case, we don't need to divide, just return as usual.
- watch the reference video for a better understanding.