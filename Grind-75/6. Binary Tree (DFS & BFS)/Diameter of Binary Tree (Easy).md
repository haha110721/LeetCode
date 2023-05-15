Diameter of Binary Tree (Easy)
===

Problem: https://leetcode.com/problems/diameter-of-binary-tree/

---

```python
Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

1. (還是有點不懂)    
講解：https://www.youtube.com/watch?v=bkxqA8Rfv04
```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        res = [0]
        
        def height(root):
            if root is None:
                return -1
            
            left, right = height(root.left), height(root.right)
            res[0] = max(res[0], left + right + 2) # 更新 diameter

            return 1 + max(left, right)

        height(root)
        return res[0]
```
