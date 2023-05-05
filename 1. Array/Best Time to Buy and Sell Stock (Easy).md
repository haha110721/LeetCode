Best Time to Buy and Sell Stock (Easy)
===

Problem: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
---

1. (我沒想到) min, max
```python
# time: O(n), space: O(1)

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        res = 0
        buy = prices[0]
        for i in prices:
            buy = min(buy, i) # 選擇 prices 中最小的
            res = max(res, i - buy) # 找到價差最大的
        return res
```

2. two pointer
```python
# time: O(n), space: O(1)

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxgap = 0
        left, right = 0, 1

        while right < len(prices):
            if prices[left] < prices[right]:
                maxgap = max(maxgap, prices[right] - prices[left])
                right += 1
            else:
                left, right = right, right + 1

        return maxgap
```        

