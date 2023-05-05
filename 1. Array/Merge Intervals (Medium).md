Merge Intervals (Medium)
===

Problem: https://leetcode.com/problems/merge-intervals/

---

1.
```python
# time: O(nlogn), space: O(n), use sort method to a list costs O(nlogn)

class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort()
        
        res = [intervals[0]]
        
        for i in range(1, len(intervals)):
            if res[-1][1] < intervals[i][0]: # 沒有重疊
                res.append(intervals[i])
            else: # 有重疊
                res[-1] = [min(res[-1][0], intervals[i][0]), max(res[-1][1], intervals[i][1])]
                
        return res 
```
