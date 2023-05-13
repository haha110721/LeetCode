Letter Combinations of a Phone Number (Medium)
===

Problem: https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/

---

# 1.
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if len(digits) == 0:
            return []
        
        res = []
        phone = {
            "2": 'abc',
            "3": 'def',
            "4": 'ghi',
            "5": 'jkl',
            "6": 'mno',
            "7": 'pqrs',
            "8": 'tuv',
            "9": 'wxyz'
        }

        def backtrack(combination, digits):
            if not digits:
                res.append(combination)
                return

            for i in phone[digits[0]]:
                backtrack(combination + i, digits[1:])

        backtrack("", digits)

        return res
```
