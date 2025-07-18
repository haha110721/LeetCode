Rotting Oranges (Medium)
===

Problem: https://leetcode.com/problems/rotting-oranges/description/

---

1. BFS
```python
from collections import deque

class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        fresh_count = 0
        rotten = deque() # queue with rotten oranges (for BFS)

        row = len(grid)
        col = len(grid[0])

        # visit every cell in grid
        for r in range(row):
            for c in range(col):
                if grid[r][c] == 2:
                    rotten.append((r, c))
                elif grid[r][c] == 1:
                    fresh_count += 1

        minute_pass = 0

        # 開始感染
        while rotten and fresh_count > 0:
            minute_pass += 1
            
            for _ in range(len(rotten)): # 在同一個 minute，每一個 rotten 都會開始感染
                x, y = rotten.popleft()
                for dx, dy in ((1, 0), (-1, 0), (0, 1), (0, -1)):
                    new_x = x + dx
                    new_y = y + dy

                    if 0 <= new_x < row and 0 <= new_y < col and grid[new_x][new_y] == 1:
                        fresh_count -= 1
                        grid[new_x][new_y] = 2
                        rotten.append((new_x, new_y))
            

        return minute_pass if fresh_count == 0 else -1
```        
