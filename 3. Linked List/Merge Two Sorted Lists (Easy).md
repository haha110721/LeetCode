Merge Two Sorted Lists (Easy)
===

Problem: https://leetcode.com/problems/merge-two-sorted-lists/

---

1. linked list
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# time: O(n+m), space: O(1)

class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        temp = dummy # dummy 不會動，所以 ans 要返回 dummy.next

        while list1 and list2: # 當兩邊都還有值
            if list1.val < list2.val:
                temp.next = list1 # 因為他是指到 id，不是指到 val
                list1 = list1.next
            elif list1.val >= list2.val:
                temp.next = list2
                list2 = list2.next
            temp = temp.next # 跳下一個 temp 準備繼續指

        if list1: # 如果只剩 list1 有值
            temp.next = list1
        elif list2: # 如果只剩 list2 有值
            temp.next = list2
```          

        return dummy.next
