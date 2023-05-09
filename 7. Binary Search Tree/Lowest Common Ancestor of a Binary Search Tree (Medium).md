Lowest Common Ancestor of a Binary Search Tree (Medium)
===

Problem: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/

Compare: [Lowest Common Ancestor of a Binary Tree (Medium)]  
Problem: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/  
My_GitHub: https://github.com/haha110721/Grind-75/edit/main/6.%20Binary%20Tree%20(DFS%20%26%20BFS)/Lowest%20Common%20Ancestor%20of%20a%20Binary%20Tree%20(Medium).md

---

1. binary tree，遞迴
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if root.val == p.val or root.val == q.val: # 如果 root 等於其中一個 p or q，那他就是答案(因為從上而下開始找)
            return root # root 代表第一個 node

        elif (p.val < root.val < q.val) or (q.val < root.val < p.val):
            return root

        elif p.val < root.val and q.val < root.val: # 如果 p、q 都小於 root，要往左邊走
            return self.lowestCommonAncestor(root.left, p, q)

        else:
            return self.lowestCommonAncestor(root.right, p, q)
```

2. 迴圈
```python
# time: O(h), space: O(1)

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        while True:
            if root.val > p.val and root.val > q.val:
                root = root.left
            elif root.val < p.val and root.val < q.val:
                root = root.right
            else:
                return root
```
