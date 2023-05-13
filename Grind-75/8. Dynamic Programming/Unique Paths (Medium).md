Unique Paths (Medium)
===

Problem: https://leetcode.com/problems/unique-paths/description/

---

1. DP
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [[1 for _ in range(n)] for _ in range(m)]

        for j in range(1, n):
            for i in range(1, m):
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1]

        return dp[m - 1][n - 1]
```
