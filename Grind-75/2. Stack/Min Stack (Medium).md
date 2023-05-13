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
        """
        取得最上層的數字
        """

        return self.stack[-1]

    def getMin(self) -> int:
        return min(self.stack)
```        

2. 用兩個 list
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minstack = [] 

    def push(self, val: int) -> None:
        self.stack.append(val)
        if self.minstack:
            val = min(self.minstack[-1], val)
        self.minstack.append(val) # 存這個時候最小的數

    def pop(self) -> None:
        self.stack.pop()
        self.minstack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minstack[-1]



# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
