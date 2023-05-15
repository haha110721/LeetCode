Clone Graph (Medium)
===

Problem: https://leetcode.com/problems/clone-graph/

---

```python
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
```

1.
```python
class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        alreadyclone = {}

        def clone(node):
            if node in alreadyclone:
                return alreadyclone[node] # return copy 的東東
            
            copy = Node(node.val)
            alreadyclone[node] = copy
            for neighbor in node.neighbors:
                copy.neighbors.append(clone(neighbor)) # 這邊要做 dfs
            return copy
        
        return clone(node) if node else None
```





