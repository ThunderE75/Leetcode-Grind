---
date: 2025-03-07
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/find-missing-and-repeated-values/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---
### Intuition
- Can be solved either by A Frequency Array or a Hash Set
- $ or we can use Math

> [!info] References
> - [Math Approach - LeetCode](https://leetcode.com/problems/find-missing-and-repeated-values/solutions/6503987/counting-math-python-c-java-js-c-go-swift)
> - [Find Missing and Repeated Values - Leetcode 2965 - Python - YouTube](https://youtu.be/LQGmWiDuTw8)
### Editorial
At first glance, this problem might seem to require tracking frequencies, but there's a more elegant mathematical approach. In a perfect sequence from 1 to n2, every number appears exactly once. However, in our given sequence, one number appears twice, and another number is missing. Let’s define the repeated number as x and the missing number as y.

Instead of explicitly counting occurrences, we can leverage basic mathematical properties of numbers. The sum of all numbers in a proper sequence from 1 to n2 can be computed using the formula:
$$perfectSum=2n2⋅(n2+1)​​$$
Similarly, the sum of the squares of these numbers follows this formula:
$$perfectSqrSum=6n2⋅(n2+1)⋅(2n2+1)$$Now, if we compute the sum of numbers in our given grid (sum) and compare it with perfectSum, we can express their relationship as:
$$sum=perfectSum+x−y​$$
This tells us that the difference between the actual sum and the perfect sum gives us:
$$sumDiff=x−y$$Similarly, if we compute the sum of squares from our grid (sqrSum) and compare it with **perfectSqrSum**, we get:
$$sqrDiff=x2−y2$$
Now, we recall a fundamental algebraic identity:
$$x2−y2=(x+y)⋅(x−y)$$​

Since we already know **x−y** from **sumDiff**, we can substitute it into the equation:

$$sqrDiff=(x+y)⋅sumDiff​$$

Rearranging this equation, we can solve for **x+y**:

$$x+y=sumDiffsqrDiff$$​​

Now, we have two simple equations:
$$x−y=sumDiff$$
$$x+y=sumDiffsqrDiff$$​​Solving for x and y:
$$x=2sqrDiff/sumDiff+sumDiff$$$$y=2sqrDiff/sumDiff−sumDiff$$​​This mathematical derivation translates directly into our code. We first calculate the actual sums from our grid and then compute the perfect sums using the formulas. The differences between these give us sumDiff and squareDifference, which we can plug into our final formulas to get the repeating and missing numbers.

> [!Note] Note 
> One important implementation detail is the use of long instead of int for our calculations. This is crucial because when we're dealing with squares of numbers, we can easily exceed the integer range.
### Optimized Solution
```java

```
### Follow Up Solution
```java fold title="Math Solution"
class Solution {
  public int[] findMissingAndRepeatedValues(int[][] grid) {
    int n = grid.length;
    int totalLength = n * n;

    long expectedSum = (long) totalLength * (totalLength + 1) / 2;
    long expectedSumSquares = (long) totalLength * (totalLength + 1) * (2 * totalLength + 1) / 6;

    long actualSum = 0, actualSumSquares = 0;

    for (int i = 0; i < n; i++) {
      for (int j = 0; j < n; j++) {
        actualSum += grid[i][j];
        actualSumSquares += (long) grid[i][j] * grid[i][j];
      }
    }

    // a - b
    long diffSum = actualSum - expectedSum;

    // a² - b²
    long diffSumSquares = actualSumSquares - expectedSumSquares;

    // a + b = (a² - b²) / (a - b)
    long sumAB = diffSumSquares / diffSum;

    // Now we can find a and b
    int a = (int) ((sumAB + diffSum) / 2);
    int b = (int) ((sumAB - diffSum) / 2);

    return new int[] { a, b };
  }
}
```
### Initial Solution
```java title="Basic HashSet Approach"
class Solution {
    public int[] findMissingAndRepeatedValues(int[][] grid) {
        int n = grid.length;
        int[] res = new int[2];
        HashSet<Integer> set = new HashSet<>();
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int curr = grid[i][j];
                if (!set.contains(curr))
                    set.add(curr);
                else
                    res[0] = curr;
            }
        }
        for (int i = 1; i <= n * n; i++)
            if (!set.contains(i)){
                res[1] = i;
                break;
            }
        return res;
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 