---
Date: 2025-03-24
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/time-based-key-value-store/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- 

> [!info] References
> - [Time Based Key-Value Store - Leetcode 981 - Python - YouTube](https://youtu.be/fu2cD_6E8Hw)
### Optimized Solution
```java

```
### Follow Up Solution
```java

```
### Initial Solution
```java
class TimeMap {
    HashMap<String, TreeMap<Integer, String>> db;

    public TimeMap() {
        db = new HashMap<>();
    }

    public void set(String key, String value, int timestamp) {
        if (!db.containsKey(key))
            db.put(key, new TreeMap<>());
        db.get(key).put(timestamp, value);
    }

    public String get(String key, int timestamp) {
        if (!db.containsKey(key))
            return "";
        TreeMap<Integer, String> times = db.get(key);
        Map.entry<Integer, String> entry = times.floorEntry(timestamp);
        return (entry == null) ? "" : entry.getValue();
    }
}
```
### Key Takeaways
- 

*similar to:* 
- 