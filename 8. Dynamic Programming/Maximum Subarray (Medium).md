Maximum Subarray (Medium)
===

Problem: https://leetcode.com/problems/maximum-subarray/description/

---

1. Dynamic Programming
```python
# time: O(n), space: O(1)

class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        for i in range(1, len(nums)):
            nums[i] = max(nums[i], nums[i] + nums[i-1]) # 更新原本的 list
        return max(nums)
```
