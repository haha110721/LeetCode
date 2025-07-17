Course Schedule (Medium)
===

Problem: https://leetcode.com/problems/course-schedule/description/

---

1. (要想很多下) DFS   
講解：https://www.youtube.com/watch?v=EgI5nU9etnU
```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        # 先把 cours 和這門課的 prerequisites 重新整理
        premap = {i: [] for i in range(numCourses)}
        for cours, prere in prerequisites:
            premap[cours].append(prere)

        visited = set()

        def dfs(cours): # 看這門課可不可以完成
            if cours in visited: # 已經走過了
                return False
            
            if premap[cours] == []:
                return True

            visited.add(cours)
            for prere in premap[cours]:
                if not dfs(prere):
                    return False
            visited.remove(cours)
            premap[cours] = []
            return True
        
        
        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
```
