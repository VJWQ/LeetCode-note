## 用数组实现队列
在使用数组表示队列时，首先要创建一个长度为MAXSIZE的数组作为队列。因为MAXSIZE是数组的长度，MAXSIZE-1是队列的最大下标。  
在队列中，除了用一组地址连续的存储单元依次存储从队首到队尾的元素外，还需要附设两个整型变量head和tail分别指示队首和队尾的位置。

主要包含三个操作：
- 初始化队列
- enqueue()向队尾插入元素
- dequeue()删除并返回队首元素  

每次元素入队时，tail向后移动；每次元素出队时，head向后移动。

可以将队列视作一个类，通过成员变量数组来表示一组地址连续的存储单元，再定义两个成员变量head和tail，将队列的基本操作定义成类的方法。  
（注意：为了将重点放在实现队列上，做了适当简化。示范队列仅支持整数类型，若想实现泛型，可用反射机制和object对象传参；此外，可多做安全检查并抛出异常）

### Python

```python
class MyQueue(object):

    def __init__(self):
        # do some intialize if necessary
        self.MAXSIZE = 4
        self.queue = [0] * self.MAXSIZE
        self.head, self.tail = 0, 0

    # @param {int} item an integer
    # @return nothing
    def enqueue(self, item):
        queue = self.queue 

        # 队列满 
        if self.tail == self.MAXSIZE:
            return 

        queue[self.tail] = item 
        self.tail += 1 


    # @return an integer
    def dequeue(self):
        queue = self.queue 

        ## 队列为空
        if self.head == self.tail:
            return -1 

        item = queue[self.head]
        self.head += 1 
        return item 
```

### Java
```java
public class MyQueue {
    public int head, tail;
    public int MAXSIZE = 100000;
    public int[] queue = new int[MAXSIZE];

    public MyQueue() {
        head = tail = 0;
        // do initialize if necessary
    }

    public void enqueue(int item) {      
        // 队列已满
        if(tail == MAXSIZE){
            return ;
        }

        queue[tail++] = item;
    }

    public int dequeue() {
        // 队列为空
        if (head == tail){
            return -1;
        }

        return queue[head++];      
    }
}
```
