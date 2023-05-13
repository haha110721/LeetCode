Sort Colors (Medium)
===

Problem: https://leetcode.com/problems/sort-colors/

---

1. two pointer
```python
# time: O(n), space: O(1)

class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """

        left, mid, right = 0, 0, len(nums) - 1 # 三個指針分別表示左、當前和右
        while mid <= right:
            if nums[mid] == 0: # 表示左邊放好了 
                nums[left], nums[mid] = nums[mid], nums[left]
                left += 1
                mid += 1
            elif nums[mid] == 2: # 表示右邊放好了
                nums[right], nums[mid] = nums[mid], nums[right]
                right -= 1
            else: # nums[mid] == 1
                mid += 1
        return nums
```
