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
```python
# time: O(n), space: O(1)

class Solution:
    def isPalindrome(self, s: str) -> bool:
    	i, j = 0, len(s) - 1
    	while i < j:
    		a, b = s[i].lower(), s[j].lower()
    		if a.isalnum() and b.isalnum():
    			if a != b: return False
    			else:
    				i, j = i + 1, j - 1
    				continue
    		i, j = i + (not a.isalnum()), j - (not b.isalnum())
    	return True
```      
