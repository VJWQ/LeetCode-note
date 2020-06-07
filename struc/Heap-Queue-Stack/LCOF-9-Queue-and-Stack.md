# Use two stacks to construct a queue
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

# Use two queues to construct a stack

