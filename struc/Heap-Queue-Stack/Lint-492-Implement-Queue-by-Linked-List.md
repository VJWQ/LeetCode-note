### Python

```python
class Node():
    def __init__(self, _val):
        self.next = None
        self.val = _val

class MyQueue:
    def __init__(self):
        self.first = None
        self.last = None
        
    """
    @param: item: An integer
    @return: nothing
    """
    def enqueue(self, item):
        # write your code here
        if self.first is None:
            self.first = Node(item)
            self.last = self.first
        else:
            self.last.next = Node(item)
            self.last = self.last.next
            
    """
    @return: An integer
    """
    def dequeue(self):
        # write your code here
        if self.first:
            item = self.first.val
            self.first = self.first.next
            return item
            
        return None
```
