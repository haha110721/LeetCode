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
        if not root:  # reach a dead end, I didn't find anything here
            return None

        if root == p or root == q:  # 如果當前節點是 p 或 q → 回傳這個節點
            return root

        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)

        # 如果只有左邊或右邊有找到目標節點，就把那個找到的往上回傳；但如果左右兩邊都有找到，代表這個 root 就是他們的共同祖先（LCA）
        if not left:
            return right
        if not right:
            return left
        return root
```

        

                
