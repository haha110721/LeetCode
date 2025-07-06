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
```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        parent = [i for i in range(n)]
        rank = [1] * n  # store 這個 root 連接的 node 數量

        def find(n1):
            res = n1

            while res != parent[res]:
                parent[res] = parent[parent[res]]
                res = parent[res]

            return res

        def union(n1, n2):
            p1, p2 = find(n1), find(n2)

            if p1 == p2:  # 當 parent 一樣表示他們已經被連接在一起了
                return 0

            if rank[p2] > rank[p1]:
                parent[p1] = p2  # p2 是 p1 的 parent
                rank[p2] += rank[p1]
            else:
                parent[p2] = p1
                rank[p1] += rank[p2]
            return 1

        res = n
        for n1, n2 in edges:
            res -= union(n1, n2)  # 全部的 node 數量減去連接幾次就是剩幾個 connected component
        return res
```
