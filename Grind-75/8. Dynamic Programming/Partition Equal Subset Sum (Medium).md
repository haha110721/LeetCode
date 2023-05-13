Partition Equal Subset Sum (Medium)
===

Problem: https://leetcode.com/problems/partition-equal-subset-sum/description/

---

1.
```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        if sum(nums) % 2:
            return False

        target = sum(nums) // 2

        dp = [False] * (target + 1)
        dp[0] = True

        for n in nums:
            for i in range(target, n-1, -1): # when n = 1, i = 11...1
                if dp[target]:
                    return True

                dp[i] = dp[i] or dp[i - n]

        return dp[target]
```
                
        
