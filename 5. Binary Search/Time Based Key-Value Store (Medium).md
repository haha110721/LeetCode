Time Based Key-Value Store (Medium)
===

Problem: https://leetcode.com/problems/time-based-key-value-store/

---

1. Hash Table + Binary Search
```python
# time: O(logn), space: O(n)

import collections

class TimeMap:
    def __init__(self):
        self.map = collections.defaultdict(list)

    def set(self, key: str, value: str, timestamp: int) -> None:
        self.map[key].append([value, timestamp])        

    def get(self, key: str, timestamp: int) -> str: 
        # 用 binary search
        res = ""

        matches = self.map[key]
        left, right = 0, len(matches) - 1
        while left <= right:
            mid = (left + right) // 2
            if matches[mid][1] <= timestamp:
                res = matches[mid][0]
                left = mid + 1
            else:                
                right = mid - 1
                
        return res


# Your TimeMap object will be instantiated and called as such:
# obj = TimeMap()
# obj.set(key,value,timestamp)
# param_2 = obj.get(key,timestamp)
```
