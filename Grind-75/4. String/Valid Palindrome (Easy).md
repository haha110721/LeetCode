Valid Palindrome (Easy)
===

Problem: https://leetcode.com/problems/valid-palindrome/

---

1. 用正則
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        new_s = ''.join(re.findall(r'[A-Za-z0-9]', s))
        return new_s.lower() == new_s[::-1].lower()
```

2. two pointer
   
2-1.
```python
# time: O(n), space: O(1)

class Solution:
    def isPalindrome(self, s: str) -> bool:
        i, j = 0, len(s) - 1

        while i < j:
            a, b = s[i].lower(), s[j].lower()
            if a.isalnum() and b.isalnum():
                if a != b:
                    return False
                else:
                    i += 1
                    j -= 1
            else:
                i += (not a.isalnum()) # 盡量不要這樣用
                j -= (not b.isalnum())

        return True
```

2-2.
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        i, j = 0, len(s) - 1

        while i < j:
            while (s[i].isalnum()==False) and i < j: # 不然怕它一直加一直減會違反 i < j
                i += 1
            while (s[j].isalnum()==False) and i < j:
                j -= 1

            if s[i].lower() != s[j].lower():
                return False
            else:
                i, j = i+1, j-1

        return True
```
