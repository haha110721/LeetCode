Binary Tree Level Order Traversal (Medium)
===

Problem: https://leetcode.com/problems/binary-tree-level-order-traversal/description/

Compare: [Binary Tree Right Side View (Medium)].  
Problem: https://leetcode.com/problems/binary-tree-right-side-view/description/.   
My_GitHub: https://github.com/haha110721/Grind-75/blob/main/6.%20Binary%20Tree%20(DFS%20%26%20BFS)/Binary%20Tree%20Right%20Side%20View%20(Medium).md

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
        
