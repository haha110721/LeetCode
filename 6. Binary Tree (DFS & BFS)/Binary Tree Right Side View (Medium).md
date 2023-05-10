Binary Tree Right Side View (Medium)
===

Problem: https://leetcode.com/problems/binary-tree-right-side-view/description/

Compare: [Binary Tree Level Order Traversal (Medium)]  
Problem: https://leetcode.com/problems/binary-tree-level-order-traversal/description/.   
My_GitHub: https://github.com/haha110721/Grind-75/blob/main/6.%20Binary%20Tree%20(DFS%20%26%20BFS)/Binary%20Tree%20Level%20Order%20Traversal%20(Medium).md. 

---

1. BFS
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right


class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []

        queue = collections.deque([root]) # 先取出第一個 root
        res = []

        while queue:
            level = [] # 放每一層的資料
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            res.append(level[-1])
        return res
```
        






