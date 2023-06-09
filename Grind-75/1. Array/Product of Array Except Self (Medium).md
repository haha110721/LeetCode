Product of Array Except Self (Medium)
===

problem: https://leetcode.com/problems/product-of-array-except-self/

---

1. prefixSum，前積*後積
```python
# time: O(n), space: O(1)

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1]*len(nums)
        pre = 1
        post= 1
        
        # 前積
        for i in range(len(nums)): # id = 0, 1, 2, 3
            res[i] *= pre # 先計算那個值之前的數的積
            pre *= nums[i] # 計算新的 prefix 值，把自己也乘上去，供下個迴圈要相乘用
        
        # 後積
        for j in range(len(nums)-1, -1, -1): # id = 3, 2, 1, 0
            res[j] *= post
            post *= nums[j]
        
        return res
```

2. 和 1. 一樣，只是用一個 for 而已
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        output_list = [1] * len(nums)
        prefix_poduct = suffix_poduct = 1
        for index, number in enumerate(nums):
            output_list[index] *= prefix_poduct
            prefix_poduct *= number
            output_list[-1 - index] *= suffix_poduct
            suffix_poduct *= nums[-1 - index]

        return output_list
```
