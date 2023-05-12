Subsets (Medium)
===

Problem: https://leetcode.com/problems/subsets/description/

---

1. 
```python
# time: O(n*2^n), space: O(n)

class Solution:
    def process(self, res, current, nums, index): 
        res.append(list(current))

        for i in range(index, len(nums)):
            current.append(nums[i])
            self.process(res, current, nums, i + 1) # index 用來做牆壁
            current.pop()

    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        current = []
        index = 0
        self.process(res, current, nums, index)

        return res
```

2.
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = [[]] 
        for num in nums:
            res += [item + [num] for item in res]
        return res
```
