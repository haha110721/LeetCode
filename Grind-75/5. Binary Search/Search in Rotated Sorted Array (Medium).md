Search in Rotated Sorted Array (Medium)
===

Problem: https://leetcode.com/problems/search-in-rotated-sorted-array/description/

---

1.
```python
# time: O(logn), space: O(1)

class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1        
        
        while left <= right:
            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            if nums[left] <= nums[mid]: # 找有序的
                if nums[left] <= target < nums[mid]: # 找這中間的數
                    right = mid - 1
                else:
                    left = mid + 1
            else: # 如果已經亂掉了
                if nums[mid] < target <= nums[right]: # 找另外一邊的數
                    left = mid + 1
                else:
                    right = mid - 1
        return -1
```
