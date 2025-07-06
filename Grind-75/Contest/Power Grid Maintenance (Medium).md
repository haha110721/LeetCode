Power Grid Maintenance (Medium)
===

Problem: https://leetcode.com/problems/power-grid-maintenance/description/

---

1. 圖論 + Union-Find（並查集）+ 動態查詢
```python
class UnionFind:
    def __init__(self, size):
        self.parent = [i for i in range(size+1)]

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        px = self.find(x)
        py = self.find(y)
        if px != py:
            if px < py:
                self.parent[py] = px
            else:
                self.parent[px] = py

class Solution:
    def processQueries(self, c: int, connections: List[List[int]], queries: List[List[int]]) -> List[int]:
        uf = UnionFind(c)

        for u, v in connections:
            uf.union(u, v)

        grid_online = {}
        station_online = set(range(1, c + 1))

        for station in range(1, c + 1):
            root = uf.find(station)
            if root not in grid_online:
                grid_online[root] = []
            heapq.heappush(grid_online[root], station)  # 建立 grid_online，表示誰有同一個 root。ex. grid_online = {1: [2, 3, 4, 5]}

        res = []

        for query in queries:
            qtype, x = query

            if qtype == 1:
                if x in station_online:
                    res.append(x)
                else:
                    root = uf.find(x)
                    heap = grid_online[root]

                    while heap and heap[0] not in station_online:
                        heapq.heappop(heap)  # 清除 heap 裡面已經 offline 的 station

                    if heap:
                        res.append(heap[0])
                    else:
                        res.append(-1)

            elif qtype == 2:
                if x in station_online:
                    station_online.remove(x)

        return res
```
