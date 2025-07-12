Construct Binary Tree from Preorder and Inorder Traversal (Medium)
===

Problem: https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/

---

```python
Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

1.
講解：https://www.youtube.com/watch?v=ihj4IQGZ2zc
```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        if not preorder or not inorder:
            return None
        
        root = TreeNode(preorder[0]) # root 一定是 preorder 的第一個
        mid = inorder.index(preorder[0]) # 用 inorder 可以看出哪邊是 left tree 哪邊是 right tree
        root.left = self.buildTree(preorder[1:(mid + 1)], inorder[:mid]) # 因為左邊右邊 preorder inorder走過的個數會一樣
        root.right = self.buildTree(preorder[(mid + 1):], inorder[(mid + 1):])
        return root
```
