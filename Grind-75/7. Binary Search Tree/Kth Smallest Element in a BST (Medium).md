Kth Smallest Element in a BST (Medium)
===

Problem: https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/

---

1. Inorder traversal 的概念，用 stack
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right


class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        res = []
        while stack or root:
            while root:
                stack.append(root)
                root = root.left # 把左邊的 node 都收起來
            root = stack.pop() # 再把最下面最左邊的取出
            res.append(root)
            root = root.right
        return res[k-1].val
```

2. recursive inorder traversal
```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        res = []

        def inorder(node):
            if not node:
                return 
            
            inorder(node.left)
            
            if len(res) == k:
                return 
            res.append(node.val) # ?????不知道為什麽這個放這邊
            
            inorder(node.right)
        
        inorder(root)
        return res[-1]
```


