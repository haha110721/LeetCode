Split BST (Medium)
===

Problem: https://leetcode.com/contest/weekly-contest-70/problems/split-bst/description/

---

1. 遞迴
```python
# time: O(h)，其中 h 是樹的高度
    # 最壞為 O(n)（退化成鏈狀），最好為 O(log n)（平衡樹）
# space: O(h)，來自遞迴的 call stack

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# 根節點值 ≤ target
# → 根節點會屬於左子樹
# → 遞迴切分右子樹，然後把回傳的左子樹接到 root 的右邊

# 根節點值 > target
# → 根節點會屬於右子樹
# → 遞迴切分左子樹，然後把回傳的右子樹接到 root 的左邊

class Solution:
    def splitBST(self, root: TreeNode, target: int) -> List[Optional[TreeNode]]:
        if not root:
            return [None, None]

        if root.val <= target:
            # root 應該歸到左邊的 BST
            leftSubtree, rightSubtree = self.splitBST(root.right, target)  # 繼續判斷右子樹
            root.right = leftSubtree  # 將切出來 ≤ target 的部分接回來
            return [root, rightSubtree]
        else:
            # root 應該歸到右邊的 BST
            leftSubtree, rightSubtree = self.splitBST(root.left, target)
            root.left = rightSubtree  # 將 > target 的部分接回來
            return [leftSubtree, root]
```
