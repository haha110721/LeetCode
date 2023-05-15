Minimum Height Trees (Medium)
===

Problem: https://leetcode.com/problems/minimum-height-trees/description/

---

1. (沒有全懂)
```python
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        # 如果想要找最矮的 tree，那 root 一定是在中間，如果是邊邊的(leaves)，會把整個 tree 拉很長
        # 所以概念就是，把葉子一個一個剪光，剩下的就是中間的 node

        if n == 1:
            return [0]

        graph = defaultdict(list)
        for u, v in edges: # 把誰跟誰的關係寫清楚
            graph[u].append(v)
            graph[v].append(u)

        leaves = [x for x in graph.keys() if len(graph[x]) == 1]
        pre_leaves = leaves
        while leaves:
            new_leaves = []
            for i in leaves:
                if not graph[i]:
                    return leaves # ?????
                neighbor = graph[i].pop() # 剪掉
                graph[neighbor].remove(i)
                if len(graph[neighbor]) == 1:
                    new_leaves.append(neighbor)
            pre_leaves, leaves = leaves, new_leaves # ?????
        return pre_leaves # ?????
```
