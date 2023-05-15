Combination Sum (Medium)
===

Problem: https://leetcode.com/problems/combination-sum/description/

---

1. backtrack
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        find = []

        def backtrack(tempsum, start):
            if tempsum == target:
                res.append(find[:])
                return 
            
            if tempsum > target:
                return

            for i in range(start, len(candidates)):
                find.append(candidates[i])
                backtrack(tempsum + candidates[i], i) # tempsum + candidates[i] 會去看是不是總和等於 target 了
                find.pop()
        
        backtrack(0, 0)
        return res
```
