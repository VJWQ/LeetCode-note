Difference between DFS and BFS: stack and queue.  
区别DFS和BFS的不是栈和队列，而是在访问一个结点的时候是只把它相邻的下一个结点压进去还是把它相邻的所有节点压进去

# DFS: use stack
Stack is visualized as a vertical structure and hence has depth - DFS.  

## **Stack:** Last-In/First-Out (LIFO) or First-In/Last-Out (FILO) manner. 
- **empty():** Returns whether the stack is empty.  
- **size():** Returns the size of the stack.  
- **top():** Returns a reference to the top most element of the stack.  
- **push(g):** Adds the element ‘g’ at the top of the stack.  
- **pop():** Deletes the top most element of the stack.  



# BFS: use queue
Queue can be generally thought as horizontal in structure (breadth/width can be attributed to it) - BFS.  
队列（queue）是一种采用先进先出（FIFO，first in first out）策略的抽象数据结构。比如生活中排队，总是按照先来的先服务，后来的后服务。队列在数据结构中举足轻重，其在算法中应用广泛，最常用的就是在宽度优先搜索(BFS）中，记录待扩展的节点。  

队列内部存储元素的方式，一般有两种，数组（array）和链表（linked list）。两者的最主要区别是：
- 数组对随机访问有较好性能。
- 链表对插入和删除元素有较好性能。

## **Queue:** First In First Out (FIFO) manner. 
- **Enqueue:** Adds an item to the queue. Overflow if the queue is full.  
- **Dequeue:** Removes an item from the queue. The items are popped in the same order in which they are pushed. Underflow if the queue is empty.  
- **Front:** Get the front item from queue.  
- **Rear:** Get the last item from queue.  

```java
public void levelTraverse(TreeNode root) {
		if (root == null) {
			return;
		}
		LinkedList<TreeNode> queue = new LinkedList<>();
		queue.offer(root);
		while (!queue.isEmpty()) {
			TreeNode node = queue.poll();
			System.out.print(node.val+"  ");
			if (node.left != null) {
				queue.offer(node.left);
			}
			if (node.right != null) {
				queue.offer(node.right);
			}
		}
	}
```
