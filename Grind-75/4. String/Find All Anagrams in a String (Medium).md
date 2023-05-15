Find All Anagrams in a String (Medium)
===

Problem: https://leetcode.com/problems/find-all-anagrams-in-a-string/description/

---

1. 
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        left = 0
        memo = {}
        res = []

        # 將 p 字串裡面的字母算出個別有幾個
        for token in p:
            if token in memo:
                memo[token] += 1
            else:
                memo[token] = 1

        for right, token in enumerate(s):
            if token in memo: # 在 s 裡面如果遇到 p 有的字母，那 memo 裡面要記錄少一個
                memo[token] -= 1
            else:
                memo[token] = -1

            while memo[token] < 0: # 如果發現這個字母已經不對了，開始 while 工作
                memo[s[left]] += 1
                left += 1
            
            if (right - left + 1) == len(p):
                res.append(left)
        
        return res
```
