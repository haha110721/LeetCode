String to Integer (atoi) (Medium)
===

Problem: https://leetcode.com/problems/string-to-integer-atoi/

---

1.
```python
# time: O(n), space: O(1)

class Solution:
    def myAtoi(self, s: str) -> int:
        int_max = 2147483647
        int_min = -2147483648

        res = 0
        sign = 1
        index = 0

        s = s.strip()

        if s == "":
            return 0

        if s[0] == "-":
            sign = -1

        if s[0] in set("+-"):
            index += 1

        while index < len(s) and s[index].isdigit():
            res = res*10 + int(s[index])
            index += 1

        res *= sign
        res = max(int_min, min(res, int_max))
        
        return res
```

2.
```python
class Solution:
    def myAtoi(self, str: str) -> int:
        value, state, pos, sign = 0, 0, 0, 1

        if len(str) == 0:
            return 0

        while pos < len(str):
            current_char = str[pos]
            if state == 0:
                if current_char == " ":
                    state = 0
                elif current_char == "+" or current_char == "-":
                    state = 1
                    sign = 1 if current_char == "+" else -1
                elif current_char.isdigit():
                    state = 2
                    value = value * 10 + int(current_char)
                else:
                    return 0
            elif state == 1:
                if current_char.isdigit():
                    state = 2
                    value = value * 10 + int(current_char)
                else:
                    return 0
            elif state == 2:
                if current_char.isdigit():
                    state = 2
                    value = value * 10 + int(current_char)
                else:
                    break
            else:
                return 0
            pos += 1

        value = sign * value
        value = min(value, 2 ** 31 - 1)
        value = max(-(2 ** 31), value)

        return value
```        
