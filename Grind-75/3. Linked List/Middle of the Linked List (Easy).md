Middle of the Linked List (Easy)
===

Problem: https://leetcode.com/problems/middle-of-the-linked-list/

---

1. 要兩個 pointer
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# time: O(n), space: O(1)

class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast, slow = head, head
        while fast and fast.next: # 看是不是跑到最後了
            fast = fast.next.next
            slow = slow.next
        return slow
```

