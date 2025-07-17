Climbing Stairs (Easy)
===

Problem: https://leetcode.com/problems/climbing-stairs/

---

1. 慢慢往前?
```python
# time: O(n), space: O(1)

class Solution:
    def climbStairs(self, n: int) -> int:
        i, j = 1, 1 # 起始

        for k in range(n-1): # 用舉例看要往前移幾次
            temp = j
            j = i + j
            i = temp
        
        return j
```

2. (XX: TLE) 遞迴
```python
class Solution(object):
    def climbStairs(self, n: int) -> int:
        if n == 1: 
            return 1
        if n == 2:
            return 2
        
        return self.climbStairs(n-1) + self.climbStairs(n-2)
```



