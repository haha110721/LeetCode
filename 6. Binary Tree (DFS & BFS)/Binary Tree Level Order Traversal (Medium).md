Binary Tree Level Order Traversal (Medium)
===

Problem: https://leetcode.com/problems/binary-tree-level-order-traversal/description/

---

1. (要想一下) BFS
```python
# time: O(n), space: O(n)

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right


import collections

class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []

        queue, output = collections.deque([root]), [] # 現在 queue 只有第一個
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft() # 取出第一個 node
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            output.append(level)

        return output
```        
        
