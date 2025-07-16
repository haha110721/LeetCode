Evaluate Reverse Polish Notation (Medium)
===

Problem: https://leetcode.com/problems/evaluate-reverse-polish-notation/

---

1. stack
```python
# time: O(n), space: O(n)

class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        num_stack = []

        for i in tokens:
            if i not in "+-*/":
                num_stack.append(int(i))
            else:
                num = num_stack.pop() # 這邊把數字取出，同時 pop 掉

                if i == "+":
                    num_stack[-1] += num
                elif i == "-":
                    num_stack[-1] -= num
                elif i == "*":
                    num_stack[-1] *= num
                else:
                    num_stack[-1] = int(num_stack[-1] / num)
                    
        return num_stack[0]         
```
