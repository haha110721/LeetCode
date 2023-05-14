01 Matrix (Medium)
===

Problem: https://leetcode.com/problems/01-matrix/description/

---

1.
```python
class Solution:
    def updateMatrix(self, mat: List[List[int]]) -> List[List[int]]:
        row = len(mat)
        col = len(mat[0])
        dist = [[float('inf') for _ in range(col)] for _ in range(row)]

        # 從上、左先看是不是 0，計算跟 0 的距離
        for i in range(row):
            for j in range(col):
                if mat[i][j] == 0:
                    dist[i][j] = 0
                else:
                    top = dist[i - 1][j] if i >= 0 else float('inf')
                    left = dist[i][j - 1] if j >= 0 else float('inf')
                    dist[i][j] = min(top, left) + 1

        # 再來從下、右看是不是 0，計算跟 0 的距離
        for i in range(row-1, -1, -1):
            for j in range(col-1, -1, -1):
                if mat[i][j] == 0:
                    dist[i][j] = 0
                else:
                    bottom = dist[i + 1][j] if i + 1 < row else float('inf')
                    right = dist[i][j + 1] if j + 1 < col else float('inf')
                    dist[i][j] = min(dist[i][j], (min(bottom, right) + 1)) # we don't want to change value if top, left is less than bottom, right
        
        return dist
```
