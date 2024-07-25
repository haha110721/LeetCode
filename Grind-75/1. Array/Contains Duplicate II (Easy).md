Contains Duplicate II (Easy)
===

Problem: https://leetcode.com/problems/contains-duplicate-ii/description/?envType=study-plan-v2&envId=top-interview-150

---

Hash Table
```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        lookup = {}

        for i in range(len(nums)):
            if nums[i] in lookup and abs(lookup[nums[i]]-i) <= k:
                return True
            else:
                lookup[nums[i]] = i
        return False
```

