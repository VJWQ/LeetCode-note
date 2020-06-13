# Use two stacks to construct a queue (FIFO)
- Put elements in the first stack A;  
- **Enqueue**: directly append element at the tail of A;  
- **Dequeue**: 
  - *if the second stack B is empty*: pop out from A and add to B => Now elements in B are in reversed order => pop element from B.  
  - *if B is not empty*: directly pop element. 

```python
class CQueue:

    def __init__(self):
        self.A = []
        self.B = []

    def appendTail(self, value: int) -> None:
        # Simply adds new element at the tail
        self.A.append(value)

    def deleteHead(self) -> int:
        # Stack B is empty: not reverse the stack A yet
        if not self.B:
            if self.A:
                while self.A:
                    self.B.append(self.A.pop())
                    
            else:
                return -1
        # Stack B is not empty: directly pop out the last element
        return self.B.pop()


# Your CQueue object will be instantiated and called as such:
# obj = CQueue()
# obj.appendTail(value)
# param_2 = obj.deleteHead()
```

# Use two queues to construct a stack (FILO/LIFO)
- Put elements in the first queue;  
进栈：元素入队列A

出栈：判断如果队列A只有一个元素，则直接出队。否则，把队A中的元素出队并入队B，直到队A中只有一个元素，再直接出队。为了下一次继续操作，互换队A和队B。
- **Push**:  directly enqueue to queue A;  
- **Pop**: 
  - *if queue A only remains 1 element*: swap A and B => dequeue from queue B;  
  - *queue A has more than 1 elements*:  dequeue from A and enqueue to B till only 1 element in A => in reverse order => swap A and B => dequeue from queue B. 

```python
class StackWithTwoQueues(object):
    # Define two empty queues
    def __init__(self):
        self.A = []
        self.B = []
        
    # Push element
    def push(self, item):
        self.A.append(item)
        
    # Pop element
    def pop(self):
        if len(self.A) == 0:
            return(None)
        while(len(self.A) != 1):
            self.B.append(self.A.pop(0))
        # Swap A and B and make sure there's only 1 element in the queue to dequeue
        self.A, self.B = self.B, self.A
        return (self.B.pop())
        
#test
# output: 0 4 3 6 5 2 1
if __name__ == '__main__':
    ss = StackWithTwoQueues()
    ss.push(0)
    print(ss.pop())

    list1 = [1, 2, 3, 4]
    for i in range(4):
        ss.push(list1[i])

    for i in range(2):
        print(ss.pop())
    list2 = [5,6]
    for i in range(2):
        ss.push(list2[i])

    for i in range(4):
        print(ss.pop())
```
