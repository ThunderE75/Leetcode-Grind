---
Hardness: Easy
No.: "278"
Solution Type:
  - Binary Search
Que Type:
  - Array
Clarity: Medium
URL: https://leetcode.com/problems/first-bad-version/description/
Date: 2024-11-10T02:36
Week:
  - Week 2
Next Review: November 14, 2024
---

## Optimized Solution

[First Bad Version - YouTube](https://youtu.be/SNDE-C86n88)

```Java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int l=1; // Question is 1 indexed
        int r=n;
        
        while (l < r){
            int mid = l + (r-l)/2;
            if(isBadVersion(mid)) r = mid;
            else l = mid+1;
        }
        // We don't even need to check other things
        return l;
    }
}
```

## Assisted Solution

by Nick White
[LeetCode First Bad Version Solution Explained - Java - YouTube](https://youtu.be/86SBizUsbGY)

```java 
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int l=1; // Question is 1 indexed
        int r=n;
        
        while (l < r){
            int mid = l + (r-l)/2;
            if(isBadVersion(mid)) r = mid;
            else l = mid+1;
        }
		
        // Do not use --mid;
        // because it's evaulated on the same line
        // if (isBadVersion(mid) && !isBadVersion(mid-1)) return mid;
        if (l == r && isBadVersion(l)) return l;
        return -1;
    }
}
```

## Initial Solution

```Java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int l=1; // Question is 1 indexed
        int r=n;
        
        while (l <= r){
        int mid = l + (r-l)/2;

        // Do not use --mid;
        // because it's evaulated on the same line
        if (isBadVersion(mid) && !isBadVersion(mid-1)) return mid;
        else if(isBadVersion(mid)) r = mid;
        else l = mid+1;
        }
        return -1;
    }
}
```

```Java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        return find(n,0,n);
    }
    public int find(int n, int l, int r){
        int mid = l + (r-l)/2;
        if (isBadVersion(mid) && !isBadVersion(--mid)) return mid+1;
		
        if(isBadVersion(mid)) return find(n, l, mid-1);
        
        return find(n, mid+1, r);
    }
}
```