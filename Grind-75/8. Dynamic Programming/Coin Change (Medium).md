Coin Change (Medium)
===

Problem: https://leetcode.com/problems/coin-change/description/

---

1. Bottom Up DP (Tabulation)
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [float(inf)]*(amount + 1)
        dp[0] = 0

        for i in range(1, len(dp)): # 這個 i 等於 i 塊錢，dp 這個 list 放當 i 塊錢時需要換的零錢數
            for coin in coins:
                if coin <= i:
                    dp[i] = min(dp[i], dp[i - coin] + 1) # dp[i]: number of coins needed to make amount i
        
        if dp[amount] == float(inf):
            return -1
        
        return dp[amount]
```

