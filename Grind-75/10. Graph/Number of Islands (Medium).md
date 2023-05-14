Number of Islands (Medium)
===

Problem: https://leetcode.com/problems/number-of-islands/description/

---

1. 
```python
class Solution:
    def dfs(self, grid, i, j): # 找到 '1' 之後，擴散，把附近的 '1' 都變成 '0'，然後就會跳出這個 function
        grid[i][j] = 0
        for dr, dc in (1, 0), (-1, 0), (0, 1), (0, -1):
            row = i + dr
            col = j + dc
            if 0 <= row < len(grid) and 0 <= col < len(grid[0]) and grid[row][col] == '1':
                self.dfs(grid, row, col)

    def numIslands(self, grid: List[List[str]]) -> int:
        count = 0

        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    self.dfs(grid, i, j) # 每個格子都做，跳出 function 之後，就算找到一個 island，所以 count + 1
                    count += 1
        
        return count
```        
