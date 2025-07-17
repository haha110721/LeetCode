Min Stack (Medium)
===

Problem: https://leetcode.com/problems/min-stack/

---

1. 用一個 list
```python
class MinStack:

    def __init__(self):
        self.stack = []
        

    def push(self, val: int) -> None:
        self.stack.append(val)
        

    def pop(self) -> None:
        self.stack.pop()
        

    def top(self) -> int:
        return self.stack[-1]  # 取得最上層的數字
        

    def getMin(self) -> int:
        return min(self.stack)
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```        

2. 用兩個 list
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.min_stack = []  # 紀錄「當前狀態下」的最小值
        

    def push(self, val: int) -> None:
        '''
        把 val 放進 stack
        若 min_stack 為空或 val <= min_stack[-1]，也 push 進 min_stack
        '''

        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)
        

    def pop(self) -> None:
        '''
        如果 pop 的元素等於 min_stack[-1]，表示最小值被移除，也要從 min_stack pop 掉
        '''
        
        val = self.stack.pop()
        if val == self.min_stack[-1]:
            self.min_stack.pop()
        

    def top(self) -> int:
        return self.stack[-1]  
        

    def getMin(self) -> int:
        return self.min_stack[-1]  
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
