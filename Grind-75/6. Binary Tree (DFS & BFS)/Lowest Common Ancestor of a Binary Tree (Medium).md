Lowest Common Ancestor of a Binary Tree (Medium)
===

Problem: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/

*和 235. Lowest Common Ancestor of a Binary Search Tree (Medium) 問題比較

---

1. (要想一下) DFS
```python
# time: O(n), space: O(1)

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if not root: # reach a dead end, I didn't find anything here
            return None

        if root.val == p.val or root.val == q.val:
            return root

        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)

        if not left:
            return right
        if not right:
            return left
        return root
```

        

                
