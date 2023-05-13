Valid Anagram (Easy)
===

Problem: https://leetcode.com/problems/valid-anagram/

---

1. 直接用 sorted
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```
      
2. 用 collections
```python
import collections

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        tracker = collections.defaultdict(int)
        for x in s: tracker[x] += 1
        for x in t: tracker[x] -= 1
        return all(x == 0 for x in tracker.values())
```

3. 用 set & .count()
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        for idx in set(s):
            # Compare s.count(l) and t.count(l) for every index i from 0 to 26...
            # If they are different, return false...
            if s.count(idx) != t.count(idx):
                return False
        return True 
```
