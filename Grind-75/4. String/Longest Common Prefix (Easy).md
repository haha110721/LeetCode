Longest Common Prefix (Easy)
===

Problem: https://leetcode.com/problems/longest-common-prefix/description/

---

1.
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        res = ''
        strs = sorted(strs)
        for i in range(min(len(strs[0]), len(strs[-1]))):
            if strs[0][i] != strs[-1][i]:
                return res
            res += strs[0][i]
        return res
```
