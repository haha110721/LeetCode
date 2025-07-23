Task Scheduler (Medium)
===

Problem: https://leetcode.com/problems/task-scheduler/description/

---

1. 用數學
```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        occurrence = Counter(tasks).values() # if tasks = ["A","A","A","B","B","B"]，這會是 [3, 3]
        max_count = max(occurrence) # 出現重複的最多是有幾個
        num_most_frequent_tasks = list(occurrence).count(max_count) # 表示出現最多次數的有幾種，這會是 2

        return max((max_count - 1) * (n + 1) + num_most_frequent_tasks, len(tasks))
```

2. Heap (還不懂)
```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        count = Counter(tasks).values()
        maxheap = [-cnt for cnt in count]
        heapq.heapify(maxheap)

        q = deque()

        time = 0
        while maxheap or q:
            time += 1 # ?????
            if maxheap:
                cnt = 1 + heapq.heappop(maxheap)
                if cnt: # 如果 count 還沒變成 0，表示還有
                    q.append([cnt, time + n])
            if q and q[0][1] == time: # ?????
                heapq.heappush(maxheap, q.popleft()[0])
        
        return time
```
