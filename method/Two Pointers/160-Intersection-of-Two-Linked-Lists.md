- Two Pointers

### Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        # pA = headA
        # pB = headB
        # while pA != pB:
        #     if pA:
        #         pA = pA.next
        #     else:
        #         pA = headB
        #     if pB:
        #         pB = pB.next
        #     else:
        #         pB = headA

        # return pA
        
        '''Two Pointers'''
        pA, pB = headA, headB
        while pA != pB:
            pA = pA.next if pA else headB
            pB = pB.next if pB else headA
        return pA
```
