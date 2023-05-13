First Bad Version (Easy)
===

Problem: https://leetcode.com/problems/first-bad-version/

---

1. (我寫的) binary search
```python
# The isBadVersion API is already defined for you.
# def isBadVersion(version: int) -> bool:

class Solution:
    def firstBadVersion(self, n: int) -> int:
        i = 1
        j = n

        while i <= j:
            mid = (i + j) // 2

            if isBadVersion(mid):
                if isBadVersion(mid - 1):
                    j = mid - 1
                else:
                    return mid
            else:
                i = mid + 1            
```

2. (別人寫的) binary search
```pytohn
# time: O(logn), space: O(1)

class Solution:
    def firstBadVersion(self, n: int) -> int:
        if isBadVersion(1): # 防範第 1 號產品就是 bad version
            return 1
                    
        l = 1
        r = n
        while l+1 != r:
            mid = (l + r) // 2
            if isBadVersion(mid): # 如果是 BadVersion
                r = mid
            else: # 如果不是 BadVersion
                l = mid                
        return r
```
