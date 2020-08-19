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
## 数据流问题 Data Stream Problem
遍历一次这种场景在真实的工程环境中会经常遇到，也就是我们常说的数据流问题（Data Stream Problem）。

所谓的数据流问题，就是说，你需要设计一个在线系统，这个系统不断的接受一些数据，并维护这些数据的一些信息。比如这个问题就是在数据流中维护中点在哪儿（维护中点的意思就是提供一个接口，来获取中点）。这类问题的特点都是，你没有机会第二次遍历所有数据。类似的一些数据流问题还有：  

[数据流中位数](http://www.lintcode.com/problem/data-stream-median/)  
[数据流最大 K 项](http://www.lintcode.com/problem/top-k-largest-numbers-ii/)  
[数据流高频 K 项](http://www.lintcode.com/problem/top-k-frequent-words-ii/)  


可以使用双指针算法来解决链表中点的问题，更具体的，我们可以称之为快慢指针算法。该算法如下：  
Java:
```java
ListNode slow = head, fast = head.next;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
}

return slow;
```

Python:
```python
slow, fast = head, head.next
while fast != None and fast.next != None:
    slow = slow.next
    fast = fast.next.next

return slow
```
在上面的程序中，将快指针放在第二个节点上，慢指针放在第一个节点上，while 循环中每一次快指针走两步，慢指针走一步。这样当快指针走到头的时候，慢指针就在中点了。
