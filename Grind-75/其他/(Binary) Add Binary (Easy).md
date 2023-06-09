Add Binary (Easy)
===

Problem: https://leetcode.com/problems/add-binary/

---

1. 
```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        a = a[::-1]
        b = b[::-1]

        res = ''
        carry = 0

        for i in range(max(len(a), len(b))):
            # if out bound
            digit_a = int(a[i]) if i < len(a) else 0
            digit_b = int(b[i]) if i < len(b) else 0
            
            add = digit_a + digit_b + carry
            add_res = str(add % 2) # if 1 = 0+1 or 1+0 -> 1, if 2 = 1+1 -> 0, if 3 = 1+1+1 -> 1
            res = add_res + res # 這個順序很重要
            carry = add // 2 # 算進位

        if carry:
            res = '1' + res
        
        return res
```

2.
```python
# time: O(max(n, m)), space: O(max(n, m))

class Solution:
  def addBinary(self, a: str, b: str) -> str:
    s = []
    carry = 0
    i = len(a) - 1
    j = len(b) - 1

    while i >= 0 or j >= 0 or carry:
      if i >= 0:
        carry += int(a[i])
        i -= 1
      if j >= 0:
        carry += int(b[j])
        j -= 1
        
      s.append(str(carry % 2))
      carry //= 2

    return ''.join(reversed(s))
```



