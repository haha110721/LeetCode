Insert Interval (Medium)
===

Problem: https://leetcode.com/problems/insert-interval/

---

1.
```python
# time: O(n), space: O(1)

class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        ans = []
        
        for i in intervals:
            if newInterval[0] > i[1]: # 如果這個 newInterval 大於舊區間，把舊區間放進去
                ans.append(i) 
            elif newInterval[1] < i[0]: # 如果這個 newInterval 或是重選的 newInterval 小於舊區間，先把這個 newInterval 放進答案，再放舊區間
                ans.append(newInterval)
                newInterval = i
            else: # 如果這個 newInterval 和舊區間卡在一起，把 newInterval 重選，繼續進入迴圈
                newInterval = [min(i[0], newInterval[0]), max(i[1], newInterval[1])]
        
        ans.append(newInterval)
        return ans 
```
