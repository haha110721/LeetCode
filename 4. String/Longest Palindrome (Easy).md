Longest Palindrome (Easy)
===

Problem: https://leetcode.com/problems/longest-palindrome/

---

1. (我寫的)
```python
class Solution:
    def longestPalindrome(self, s: str) -> int:
        res = 0
        
        check_dict = {}
        for i in s:
            if i in check_dict:
                del check_dict[i]
                res += 2
            else:
                check_dict[i] = 1
        
        if check_dict:
            return res + 1
        else:
            return res
```

2. (別人寫的) set
```python
# time: O(n), space: O(n)

class Solution:
    def longestPalindrome(self, s: str) -> int:
        ss = set()

        for letter in s:
            if letter not in ss:
                ss.add(letter)
            else:
                ss.remove(letter)
        
        if len(ss) != 0:
            return len(s) - len(ss) + 1 
        else:
            return len(s) # 表示 s 的所有字母都有用到
```

3. (別人寫的)
```python
import collections

class Solution:
    def longestPalindrome(self, s):
        c = collections.Counter(s)

        output = 0 # 答案

        odd_found = False # 看不懂這個 odd_found 是幹嘛的???
        
        for count in c.values():
            if odd_found:
                if count > 1: # 數量是 2, 3, 4, 5...
                    if count % 2 == 0:
                        output += count
                    else:
                        output += count - 1
            else:
                if count % 2 == 0:
                    output += count
                else:
                    output += count
                    odd_found = True
        return output
```

