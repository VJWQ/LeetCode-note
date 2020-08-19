- Extra List
- Two Pointers


### If there are two middle nodes, return the second middle node:  
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        '''Extra List'''
        # record = []
        # cur = head
        # while cur:
        #     record.append(cur.val)
        #     cur = cur.next
        # for i in range(int(len(record)/2)):
        #     head = head.next
        # return head

        '''Fast-Slow Pointers'''
        fast = head
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        return slow
```

### If there are two middle nodes, return the first middle node:  
```python
        '''Fast-Slow Pointers'''
        fast = head.next
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        return slow
```

