Balanced Binary Tree (Easy)
===

Problem: https://leetcode.com/problems/balanced-binary-tree/

---

```python
Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

1. (我要想一下) 遞迴 
```python
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        return (self.Height(root) >= 0)

    def Height(self, root: Optional[TreeNode]) -> bool:
        if root is None:  
            return 0
        
        leftheight, rightheight = self.Height(root.left), self.Height(root.right)
        
        if leftheight < 0 or rightheight < 0 or abs(leftheight - rightheight) > 1: # 代表這個 subtree 已經不 balanced 了  
            return -1
        
        return max(leftheight, rightheight) + 1 # 是因為我現在在這個 node，所以高度會 +1
```
        






