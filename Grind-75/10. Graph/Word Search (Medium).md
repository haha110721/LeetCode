Word Search (Medium)
===

Problem: https://leetcode.com/problems/word-search/description/

---

1. DFS
```python
class Solution:
    def dfs(self, board, word, i, j, point):     
        if i < 0 or j < 0 or i >= len(board) or j >= len(board[0]) \
            or point >= len(word) or word[point] != board[i][j]:
            return False

        if point == len(word) - 1:
            return True
        
        for dr, dc in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            # since we can't use the same letter twice, change current board[i][j] to -1 before traversing further
            tmp = board[i][j]
            board[i][j] = -1

            if self.dfs(board, word, i + dr, j + dc, point + 1):
                return True

            board[i][j] = tmp
           
    def exist(self, board: List[List[str]], word: str) -> bool:
        # 先檢查 board 的字母數量夠不夠
        dict = defaultdict(int)
        for i in range(len(board)):
            for j in range(len(board[0])):
                dict[board[i][j]] += 1

        worddict = Counter(word)
        for char in worddict:
            if char not in dict or dict[char] < worddict[char]:
                return False
        
        # 這邊才開始主體
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == word[0]:
                    if self.dfs(board, word, i, j, 0):
                        return True
        return False
```
