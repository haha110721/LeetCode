Ransom Note (Easy)
===

Problem: https://leetcode.com/problems/ransom-note/

---

1. (我寫的) hash table
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        can_use = {}

        for i in magazine:
            if i in can_use:
                can_use[i] += 1
            else:
                can_use[i] = 1

        for j in ransomNote:
            if j in can_use:
                can_use[j] -= 1
            else:
                return False
        
        return all(k >= 0 for k in can_use.values())
```

2. 用 set & .count()
```python
class Solution:
    def canConstruct(self, ransomNote, magazine):
        for i in set(ransomNote):
            if magazine.count(i) < ransomNote.count(i):
                return False
        return True
```        
