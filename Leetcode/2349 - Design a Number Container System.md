---
Hardness: Medium
No.: "2349"
URL: https://leetcode.com/problems/design-a-number-container-system/description/?envType=daily-question&envId=2025-02-08
Date: 2025-02-08T21:09
Next Review: February 12, 2025
---
## Useful Video Resources

- [Design a Number Container System \| Leetcode 2349 - YouTube](https://youtu.be/rHM8m4s7G44)

## Follow Up Solution

```Java
class NumberContainers {
    HashMap<Integer,Integer> map1;
    HashMap<Integer,TreeSet<Integer>> map2;
    
    public NumberContainers() {
        map1 = new HashMap<>();     // index -> number
        map2 = new HashMap<>();     // number -> sorted set of indexes
    }
    
    public void change(int index, int number) {
        if (map1.containsKey(index)) {
            int oldNumber = map1.get(index);
            if (oldNumber == number) return;

            // Remove old index from old number's TreeSet
            map2.get(oldNumber).remove(index);
            if (map2.get(oldNumber).isEmpty()) {
                map2.remove(oldNumber);
            }
        }

        map1.put(index,number);    

        map2.putIfAbsent(number, new TreeSet<>());
        map2.get(number).add(index);
    }
    
    public int find(int number) {
        if (!map2.containsKey(number) || map2.get(number).isEmpty()) return -1;
        return map2.get(number).first();  // Get smallest index
    }
}
```

## Initial Solution

```Java
class NumberContainers {

    
    public NumberContainers() {
    HashMap<Integer,Integer> map = new HashMap<>();
        
    }
    
    public void change(int index, int number) {
        map.put(index,number);    
    }
    
    public int find(int number) {
        int minIdx = -1;
        for( int i : map.keySet()){
            if (map.get(i) == number){
                minIdx = (minIdx > i) ? i : minIdx;
            }
        }
        return minIdx;
    }
}

```

## Key Takeaways

- Learn about [[Hash Set]], [[Hash Map]] 
    - [+] Keyset
    - [-]  EntrySet
    - [?] TreeSet
    - [?] Priority Queue
    - [?] .computeIfAbsent()