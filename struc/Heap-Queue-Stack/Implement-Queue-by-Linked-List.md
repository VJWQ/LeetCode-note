[Lint-492-Implement-Queue-by-Linked-List](https://www.lintcode.com/problem/implement-queue-by-linked-list/description)
## 用链表实现队列
- 链表是由多个节点构成的，一个节点由两部分组成:一个是数据域,一个是指针域。  
- 链表分为:**单链表**(只能是父节点引用子节点),**双链表**(相邻的节点可相互引用),**循环链表**(在双链表的基础上,头尾节点可相互引用)。  
- 实现链表,就是在链表里加入节点,使用节点的引用域使节点之间形成连接,可相互调用。  
- 链表队列的实现原理:首先定义一个节点类,节点类包含引用域和数据域.然后定义一个链表类,链表类形成节点间的引用关系。  

主要包含三个操作：
- 初始化队列
- enqueue()向队尾插入元素
- dequeue()删除并返回队首元素  

在队列中，只要用两个指针head和tail分别指向链表的头部和尾部即可实现基本队列功能。 

### Python

```python
class Node():
    def __init__(self, _val):
        self.next = None
        self.val = _val

class MyQueue(object):

    def __init__(self):
        # do some intialize if necessary
        self.head, self.tail = None, None

    # @param {int} item an integer
    # @return nothing
    def enqueue(self, item):
        if self.head is None:
            self.head = Node(item)
            self.tail = self.head
        else:
            self.tail.next = Node(item)
            self.tail = self.tail.next

    # @return an integer
    def dequeue(self):
        if self.head is not None:
            item = self.head.val
            self.head = self.head.next
            return item
        return -1
```
### Java
```java
class Node {
    public int val;
    public Node next;
    public Node(int _val) {
        val = _val;
        next = null;
    }
}

public class MyQueue {
    public Node head, tail;

    public MyQueue() {
        head = tail = null;
        // do initialize if necessary
    }

    public void enqueue(int item) {
        if (head == null) {
            tail = new Node(item);
            head = tail;        
        } else {
            tail.next = new Node(item);
            tail = tail.next;
        }
    }

    public int dequeue() {
        if (head != null) {
            int item = head.val;
            head = head.next;
            return item;
        }
        return -1;
    }
}
```
链表可以轻松地避免“假溢出”的问题，因为在每次需要新增元素时，只需要新建一个ListNode就可以了。 循环队列也可以解决这个问题。  
