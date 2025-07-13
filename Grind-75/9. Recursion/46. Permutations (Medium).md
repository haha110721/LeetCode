Permutations (Medium)
===

Problem: https://leetcode.com/problems/permutations/description/

---

1. (要畫圖想一下) backtracking 回溯
```python
# time: O(n × n!)
    # 全排列總共有 n! 種
    # 每一種排列都需要複製長度為 n 的 path（例如 res.append(path[:])），這個複製操作是 O(n)
# space: O(n) + O(n!)
    # 遞迴的最大深度為 n 層，因此需要 O(n) 的 call stack
    # 最後要儲存所有 n! 組排列結果，每組長度為 n，總空間為 O(n × n!)，但如果只問遞迴過程的輔助空間，會回答 O(n)

class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        '''
        假設 nums = [1, 2, 3]

        第一次呼叫：path = []
        試 num=1 → path = [1]

        再進來 → 試 num=2 → path = [1, 2]

        再進來 → 試 num=3 → path = [1, 2, 3] ✅ 長度=3，加進 res

        回溯 → pop(3) → path = [1, 2]

        繼續 → 試 num=3 → path = [1, 3]

        → 試 num=2 → path = [1, 3, 2] ✅

        接下來換試 num=2、num=3 為開頭...
        '''

        res = []

        def backtrack(path):
            if len(path) == len(nums):
                res.append(path[:])
                return

            for n in nums:
                if n in path:
                    continue  # 如果這個數字已經在 path 裡，就跳過
                
                path.append(n)
                backtrack(path)
                path.pop()  # 回到上一層時，撤銷剛剛的選擇
            
        backtrack([])
        return res
```

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
