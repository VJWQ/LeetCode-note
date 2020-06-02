Difference between DFS and BFS: stack and queue. 
# DFS: use stack
**Stack:** Last-In/First-Out (LIFO) or First-In/Last-Out (FILO) manner. 
- **empty():** Returns whether the stack is empty.  
- **size():** Returns the size of the stack.  
- **top():** Returns a reference to the top most element of the stack.  
- **push(g):** Adds the element ‘g’ at the top of the stack.  
- **pop():** Deletes the top most element of the stack.  



# BFS: use queue
**Queue:** First In First Out (FIFO) manner. 
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
