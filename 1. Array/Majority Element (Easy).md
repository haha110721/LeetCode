Majority Element (Easy)
===

Problem: https://leetcode.com/problems/majority-element/

---

1. (我要想一下) Moore’s Voting Algorithm
```python
# time: O(n), space: O(1)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        sol = None
        cnt = 0 # cnt 用作投票
        for i in nums:
            if cnt == 0:
                sol = i
            cnt += (1 if i == sol else -1)
        return sol
```

2. (time limit exceed) 暴力法
```python
time: O(n^2), space: O(1)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        for i in nums:
            counter = sum(1 for k in nums if i == k)    
            if counter > len(nums) // 2:
                return i
```                
