Flood Fill (Easy)
===

Problem: https://leetcode.com/problems/flood-fill/

---

1. 遞迴
```python
# time: O(m * n)，最多走訪每個 pixel 一次
# space: O(m * n)

class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        start_color = image[sr][sc]

        def flood(x, y):
            if x < 0 or x >= len(image) or y < 0 or y >= len(image[0]):  # 如果 index 超出範圍
                return 

            if image[x][y] == color:  # 表示染過了 
                return 
            elif image[x][y] != start_color:  # 表示染不過去 
                return
            else:
                image[x][y] = color  # 如果和 start_color 一樣，而且還沒染過，就染他

            flood(x+1, y)
            flood(x-1, y)
            flood(x, y+1)
            flood(x, y-1)
        
        flood(sr, sc)
        return image
```        
