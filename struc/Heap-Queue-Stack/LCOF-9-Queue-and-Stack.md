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
```python
class StackWithTwoQueues(object):
    #定义两个空队列
    def __init__(self):
        self.queue1 = []
        self.queue2 = []
    #入栈
    def push(self, item):
        self.queue1.append(item)
    #出栈
    def pop(self):
        if len(self.queue1) == 0:
            return(None)
        while(len(self.queue1) != 1):
            self.queue2.append(self.queue1.pop(0))
        self.queue1, self.queue2 = self.queue2, self.queue1
        return (self.queue2.pop())
#test
if __name__ == '__main__':
    ss = StackWithTwoQueues()
    list = [0, 1, 2, 3, 4]
    for i in range(5):
        ss.push(list[i])
    print(list)
    for i in range(5):
        print(ss.pop(), ',', end = '')
```
