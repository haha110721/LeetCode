Majority Element (Easy)
===

Problem: https://leetcode.com/problems/majority-element/

---

1. (我要想一下) Moore’s Voting Algorithm
          
Moore’s Voting Algorithm 假設：       
- 主要元素一定存在於陣列中，如果主要元素可能不存在，則需要額外的檢查
- 僅適用於找出單一主要元素
- 不知道主要元素實際出現多少次
     
詳解：https://cloud.tencent.com/developer/article/1600607
```python
# time: O(n), space: O(1)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        candidate = 0
        
        for num in nums:
            if count == 0:
                candidate = num
            
            if num == candidate:
                count += 1
            else:
                count -= 1
        
        return candidate
```

2. (time limit exceed) 暴力法
```python
# time: O(n^2), space: O(1)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        for i in nums:
            counter = sum(1 for k in nums if i == k)    
            if counter > len(nums) // 2:
                return i
```                

3. Sorting   
```python
# time: O(n log n)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        nums.sort()
        n = len(nums)
        return nums[n//2]
```

4. Hash Map
```python
# time: O(n)

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        app_dict = defaultdict(int) # 使用 defaultdict 表示每當訪問一個不存在的鍵時，默認值為 0
        for i in nums:
            app_dict[i] += 1
            
        for k, v in app_dict.items():
            if v > len(nums)//2:
                return k
```
