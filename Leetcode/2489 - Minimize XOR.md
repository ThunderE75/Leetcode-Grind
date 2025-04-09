---
Hardness: Medium
No.: "2489"
Solution Type:
  - ⚙️ Bit Manipulation
Que Type:
  - Binary
Clarity: Medium
URL: https://leetcode.com/problems/minimize-xor/description
Date: 2025-01-15T20:35
Week:
  - 💥Not in Curriculum
Next Review: January 19, 2025
---
## Useful Resources
- [Minimize XOR - Leetcode 2429 - Python - YouTube](https://youtu.be/xhD78PX8Nss)
## Solution
> [!info] Minimize XOR - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/minimize-xor/solutions/2648779/java-intuition-behind-logic-minimize-xor](https://leetcode.com/problems/minimize-xor/solutions/2648779/java-intuition-behind-logic-minimize-xor)  

```Java
class Solution {
    public int minimizeXor(int num1, int num2) {
        if (num1 == num2) return num1;

        int res=0;
        // Used to get no. of set bits in num2
        int avalableBits = Integer.bitCount(num2);
        
        // INT has 32 bits 
        // we move from MSB -> LSB
        for (int i = 31; i >= 0; i--){
            int currBit = (num1 >> i ) & 1;
            if (currBit == 1 && avalableBits > 0){
                res |= (1 << i);
                avalableBits--;
            }
        }

        // when there are more avalableBits then need to nullify num1 
        // we add those remaing bits at LSB (until avalableBits == 0)
        for (int i = 0; i<32; i++){
            if (avalableBits == 0) break;
            int currBit = (num1 >> i) & 1;
            if (currBit == 0){
                res |= (1 << i);
                avalableBits --; 
            }
        }

        return res;
    }
}
```
## Key Takeaways
1. `currBit = (num1 >> i ) & 1` → To get the current bit (i.e., at position `i`)
    - Rightshift it with `i` (`num >> i`) → this will move `i` to LSB
    - Then (`& 1`) will return
        - if set → 1
        - If unset → 0
2. `num |= (1 << i)` → Set a specific bit
    - Leftshift 1 by i position (`1 << i`)
    - Perform an OR operation with num → (`num |=`)
    - this will set that bit to 1 (on position i)
