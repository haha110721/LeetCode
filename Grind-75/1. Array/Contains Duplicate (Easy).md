Contains Duplicate (Easy)
===

Problem: https://leetcode.com/problems/contains-duplicate/

---

1. (time limit exceeded)
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        n = len(nums)
        for i in range(n - 1):
            for j in range(i + 1, n):
                if nums[i] == nums[j]:
                    return True
        return False
```
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        for i in set(nums):
            if nums.count(i) >= 2:
                return True
        return False
```

2. hash table
```python
# time: O(n), space: O(n)

class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dict = {}
        for i in nums:
            if i in dict:
                return True
            else:
                dict[i] = 1
        return False
```

3. sort
```python
# time: O(n log n), space: O(1)

class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort()
        left = 0
        right = 1
        
        # 先排序後，看他有沒有和下一個一樣，慢慢移動
        while right < len(nums):
            if nums[left] == nums[right]:
                return True
            else:
                left, right = right, right + 1
        
        return False
```
