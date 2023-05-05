Valid Parentheses (Easy)
===

Problem: https://leetcode.com/problems/valid-parentheses/

---

1. 用 stack 概念
```python
# time: O(n), space: O(n)

class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for i in range(len(s)):
            if stack:
                if s[i] == ")" and stack[-1] == "(" or \
                s[i] == "]" and stack[-1] == "[" or \
                s[i] == "}" and stack[-1] == "{":
                    stack.pop()
                else:
                    stack.append(s[i])
            else:
                stack.append(s[i])
        
        if stack:
            return False
        else:
            return True
```
