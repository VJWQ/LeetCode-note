[622. Design Circular Queue](https://github.com/VJWQ/LeetCode-note/blob/master/struc/Heap-Queue-Stack/622-Design-Circular-Queue.md)
## 用数组实现循环队列
队列是一种先进先出的线性表，它只允许在表的一端进行插入，而在另一端删除元素。允许插入的一端称为队尾，允许删除的一端称为队首。但是我们之前也提到了，数组实现的队列会导致“虽然数组没满，但是tail已经指向了数组末尾，返回数组已满，队列溢出的错误信号”，我们称之为“假溢出”。

为充分利用向量空间，克服"假溢出"现象的方法是：将向量空间想象为一个首尾相接的圆环，并称这种向量为循环向量。存储在其中的队列称为循环队列（Circular Queue）。循环队列是把顺序队列首尾相连，把存储队列元素的表从逻辑上看成一个环，成为循环队列。

主要包含三个操作：
- 初始化循环队列
- enqueue()向队尾插入元素
- dequeue()删除并返回队首元素

在循环队列中，除了用一组地址连续的存储单元依次存储从队首到队尾的元素外，还需要附设两个整型变量head和tail分别指示队首和队尾的位置。

可以将循环队列视作一个类，通过成员变量数组来表示一组地址连续的存储单元，再定义两个成员变量head和tail，将循环队列的基本操作定义成类的方法，**循环效果则用“模”运算实现**，以此来实现循环队列。

每当tail到达末尾的时候，将tail对MAXSIZE取模，使其回到队首。但是如果这样，队列为空和队列已满的条件都成了tail == head。为了避免这种无法判断的情况，规定当循环队列只剩一个空位的时候，就认为队列已满。这样队列已满的条件就成了 (tail + 1) % MAXSIZE == head。

### Python
```python
class MyQueue(object):

    def __init__(self):
        # do some intialize if necessary
        self.SIZE = 100000
        self.queue = [0] * self.SIZE
        self.head, self.tail = 0, 0

    # @param {int} item an integer
    # @return nothing
    # 压入队列
    def enqueue(self, item):
        queue = self.queue 

        # 队列满 
        if (self.tail + 1) % self.SIZE == self.head:
            return 

        queue[self.tail] = item 
        self.tail = (self.tail + 1) % self.SIZE


    # @return an integer
    # 弹出元素
    def dequeue(self):
        queue = self.queue 

        ## 队列为空
        if self.head == self.tail:
            return -1 

        item = queue[self.head]
        self.head = (self.head + 1) % self.SIZE
        return item 
  ```
  
  ### Java
  ```java
  public class MyQueue {
    public int head, tail;
    public int SIZE = 4;
    public int[] queue = new int[SIZE];

    public MyQueue() {
        head = tail = 0;
        // do initialize if necessary
    }
    //压入一个元素
    public void enqueue(int item) {
        // 队列已满
        if ((tail + 1) % SIZE == head){
            return ;
        }

        queue[tail++] = item;
        tail %= SIZE;
    }
    //弹出一个元素
    public int dequeue() {
        // 队列为空
        if (head == tail){
            return -1;
        }

        int item = queue[head++];
        head %= SIZE;
        return item;

    }
}
  ```

