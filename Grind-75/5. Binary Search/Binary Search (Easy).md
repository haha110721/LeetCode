Binary Search (Easy)
===

Problem: https://leetcode.com/problems/binary-search/

---

1. 暴力法
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        for i in range(len(nums)):
            if nums[i] == target:
                return i
        return -1
```

2. two pointer
```python
# time: O(logn), space: O(1)

class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target: 
                return mid
            elif nums[mid] > target: # 和中間的比，如果中間比較大，right pointer 變成中間左邊的那一個數字，繼續比
                right = mid - 1
            else:
                left = mid + 1
        
        return -1
```
