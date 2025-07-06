Power Grid Maintenance (Medium)
===

Problem:
```
You are given an integer c representing c power stations, each with a unique identifier id from 1 to c (1‑based indexing).

These stations are interconnected via n bidirectional cables, represented by a 2D array connections, where each element connections[i] = [ui, vi] indicates a connection between station ui and station vi. Stations that are directly or indirectly connected form a power grid.

Initially, all stations are online (operational).

You are also given a 2D array queries, where each query is one of the following two types:

[1, x]: A maintenance check is requested for station x. If station x is online, it resolves the check by itself. If station x is offline, the check is resolved by the operational station with the smallest id in the same power grid as x. If no operational station exists in that grid, return -1.

[2, x]: Station x goes offline (i.e., it becomes non-operational).

Return an array of integers representing the results of each query of type [1, x] in the order they appear.

Note: The power grid preserves its structure; an offline (non‑operational) node remains part of its grid and taking it offline does not alter connectivity.©leetcode


Example 1:

Input: c = 5, connections = [[1,2],[2,3],[3,4],[4,5]], queries = [[1,3],[2,1],[1,1],[2,2],[1,2]]

Output: [3,2,3]

Explanation:
Initially, all stations {1, 2, 3, 4, 5} are online and form a single power grid.
Query [1,3]: Station 3 is online, so the maintenance check is resolved by station 3.
Query [2,1]: Station 1 goes offline. The remaining online stations are {2, 3, 4, 5}.
Query [1,1]: Station 1 is offline, so the check is resolved by the operational station with the smallest id among {2, 3, 4, 5}, which is station 2.
Query [2,2]: Station 2 goes offline. The remaining online stations are {3, 4, 5}.
Query [1,2]: Station 2 is offline, so the check is resolved by the operational station with the smallest id among {3, 4, 5}, which is station 3.©leetcode
```

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
            heapq.heappush(grid_online[root], station)  # 建立最小的

        res = []

        for query in queries:
            qtype, x = query

            if qtype == 1:
                if x in station_online:
                    res.append(x)
                else:
                    root = uf.find(x)
                    heap = grid_online[root]

                    # 清除 heap 裡面已經 offline 的 station
                    while heap and heap[0] not in station_online:
                        heapq.heappop(heap)

                    if heap:
                        res.append(heap[0])
                    else:
                        res.append(-1)

            elif qtype == 2:
                if x in station_online:
                    station_online.remove(x)

        return res
```
