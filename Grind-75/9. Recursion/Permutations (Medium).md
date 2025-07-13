Permutations (Medium)
===

Problem: https://leetcode.com/problems/permutations/description/

---

1. (要畫圖想一下) backtracking 回溯
```python
class Solution:
    """
    把當前選的數字加入 path，並遞迴地嘗試下一步，直到 path 長度等於 nums 長度
    nums = [1,2,3]
    Level0: []
    Level1: [1]                 
    Level2: [1,2]    [1,3]      
    Level3: [1,2,3]  [1,3,2]  
    """
    
    def backtrack(self, res, visited, subset, nums):
        if len(subset) == len(nums):
            res.append(subset)
        
        for i in range(len(nums)):
            if i not in visited:
                visited.add(i)
                self.backtrack(res, visited, subset + [nums[i]], nums)  # 會先進入遞迴，再跳出，再進入遞迴裡面的 for 迴圈結束那次遞迴
                visited.remove(i)
    
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        visited = set()
        subset = []
        self.backtrack(res, visited, subset, nums)

        return res 
```        
