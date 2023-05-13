Reverse Linked List (Easy)
===

Problem: https://leetcode.com/problems/reverse-linked-list/

---

1. (我要想一下)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# time: O(n), space: O(1)

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        pre, curr = None, head
        while curr:
            nxt = curr.next
            curr.next = pre # 把現在的下一個指回上一個
            
            # pre, curr 繼續往前動
            pre = curr
            curr = nxt
        return pre
```
 
