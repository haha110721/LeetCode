String to Integer (atoi) (Medium)
===

Problem: https://leetcode.com/problems/string-to-integer-atoi/

---

1.
```python
# time: O(n), space: O(1)

class Solution:
    def myAtoi(self, s: str) -> int:
        int_max = 2147483647
        int_min = -2147483648

        res = 0
        sign = 1
        index = 0

        s = s.strip()

        if s == "":
            return 0

        if s[0] == "-":
            sign = -1

        if s[0] in set("+-"):
            index += 1

        while index < len(s) and s[index].isdigit():
            res = res*10 + int(s[index])
            index += 1

        res *= sign
        res = max(int_min, min(res, int_max))
        
        return res
```

2.
```python
class Solution:
    def myAtoi(self, s: str) -> int:
        i = 0

        # 1. 忽略空白
        while i < len(s) and s[i] == " ":
            i += 1
        
        if i == len(s):  # 如果全部都是空白
            return 0

        # 2. 處理正負號
        sign = 1

        if s[i] == '+':
            i += 1
        elif s[i] == '-':
            sign = -1
            i += 1

        # 3. 讀取數字
        result = 0

        while i < len(s) and s[i].isdigit():
            result = result*10 + int(s[i])
            i += 1
        
        result *= sign

        # 4. 邊界判斷
        if result < (-2**31):
            return (-2**31)
        if result > (2**31 - 1):
            return (2**31 - 1)
        return result
```        
