Number of Connected Components in an Undirected Graph (Medium)
===

video: https://www.youtube.com/watch?v=8f1XPm4WOUc     

<img width="514" alt="image" src="https://github.com/user-attachments/assets/14ae4447-4696-4579-8af7-82fba375de88" />

---

1. BFS
```python
from collections import deque, defaultdict

class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        graph = defaultdict(list)

        # 建 adjacency list
        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)

        visited = set()
        count = 0

        for node in range(n):
            if node not in visited:
                count += 1  # 發現一個新的連通塊
                queue = deque()
                queue.append(node)
                visited.add(node)

                while queue:
                    curr = queue.popleft()
                    for neighbor in graph[curr]:
                        if neighbor not in visited:
                            visited.add(neighbor)
                            queue.append(neighbor)

        return count
```

2. Union Find   
參考：https://www.youtube.com/watch?v=8f1XPm4WOUc
