Accounts Merge (Medium)
===

Problem: https://leetcode.com/problems/accounts-merge/description/

---

1. DFS + Hash map
```python
class Solution:
    def accountsMerge(self, accounts: List[List[str]]) -> List[List[str]]:
        # email_to_name = set{}
        email_graph = defaultdict(list)
        for account in accounts:
            # name = account[0]
            first_email = account[1] # 設定第一個 email 是 key
            
            for email in account[2:]: # 建立 graph
                email_graph[first_email].append(email)
                email_graph[email].append(first_email)


        visited = set()
        
        def dfs(email, temp_merge):
            # 已經遇過的話，就直接跳出
            if email in visited: 
                return
            
            # 如果沒遇過
            visited.add(email)
            temp_merge.append(email)
            for neighbor in email_graph[email]:
                if neighbor not in visited:
                    dfs(neighbor, temp_merge)
            return temp_merge


        res = []
        for account in accounts:
            name, first_email = account[0], account[1]
            if first_email not in visited:
                temp_merge = []
                dfs(first_email, temp_merge)
                res.append([name] + sorted(temp_merge))
        
        return res
```

2. 還有很多其他解法：https://leetcode.com/problems/accounts-merge/solutions/1195613/91-dfs-and-bfs-with-explanation-both-iterative-and-recursive-in-python-fast-and-easy/?orderBy=most_votes&languageTags=python
