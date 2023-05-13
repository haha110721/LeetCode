Container With Most Water (Medium)
===

Problem: https://leetcode.com/problems/container-with-most-water/

---

1.
```python
# time: O(n), space:O(1)

class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_volume = 0
        left, right = 0, len(height) - 1

        while left < right:
            if height[left] >= height[right]:
                volume = height[right] * (right - left)
                right -= 1
            else:
                volume = height[left] * (right - left)
                left += 1
            
            max_volume = max(max_volume, volume)
        return max_volume
```

