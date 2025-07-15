Invert Binary Tree (Easy)
===

Problem: https://leetcode.com/problems/invert-binary-tree/

---

1. 遞迴
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# time: O(n), space: O(h), h is the height of the binary tree

class Solution(object):
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        
        root.left, root.right = root.right, root.left
        
        # Call the function recursively for the left subtree
        self.invertTree(root.left)
        # Call the function recursively for the right subtree
        self.invertTree(root.right)
        
        return root
```        
        
