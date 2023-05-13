Implement Queue using Stacks (Easy)
===

Problem: https://leetcode.com/problems/implement-queue-using-stacks/

---

1. queue
```python
class MyQueue:

    def __init__(self):
        self.stack1 = [] # 新增資料
        self.stack2 = [] # pop 資料

    def push(self, x: int) -> None:
        while self.stack2:
            self.stack1.append(self.stack2.pop())
        
        self.stack1.append(x)

    def pop(self) -> int:
        while self.stack1:
            self.stack2.append(self.stack1.pop())

        return self.stack2.pop()

    def peek(self) -> int:
        while self.stack1:
            self.stack2.append(self.stack1.pop())

        return self.stack2[-1]

    def empty(self) -> bool:
        if self.stack1 == [] and self.stack2 == []:
            return True
        else:
            return False


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()
```
