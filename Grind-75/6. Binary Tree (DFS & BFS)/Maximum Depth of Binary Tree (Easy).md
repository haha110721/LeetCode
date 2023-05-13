Maximum Depth of Binary Tree (Easy)
===

Problem: https://leetcode.com/problems/maximum-depth-of-binary-tree/

---

1. (我要想一下) 遞迴
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# time: O(n), space: O(h)

class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        
        def dfs(root, depth):
            if not root: 
                return depth
            return max(dfs(root.left, depth + 1), dfs(root.right, depth + 1))
                       
        return dfs(root, 0)
```


