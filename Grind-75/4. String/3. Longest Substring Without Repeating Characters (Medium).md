Longest Substring Without Repeating Characters (Medium)
===

Problem: https://leetcode.com/problems/longest-substring-without-repeating-characters/

---

1. sliding window
```python
# time: O(n), space: O(m), n is the length of s and m is the length of the longest substring

class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        memo = set()
        longest = 0
        window_start, window_end = 0, 0

        while window_end < len(s):
            if s[window_end] not in memo:
                longest = max(longest, window_end - window_start + 1)
                memo.add(s[window_end])
                window_end += 1
            else:
                memo.remove(s[window_start])
                window_start += 1
        return longest
```

2. hash table
```python
# time: O(n), space: O(m)

class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        memo = {}
        longest = 0
        pointer = 0

        for id, token in enumerate(s):
            if token in memo  and pointer <= memo[token]: # ???還是沒看懂這句???
                pointer = memo[token] + 1 # pointer 指向這個之前重複的下一個位置
            else:
                longest = max(longest, id - pointer + 1)
            memo[token] = id
        return longest
```
