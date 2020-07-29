The definition of a binary search tree is that for every node, all the values of the left branch are less than the value at the root, and all the values of the right branch are greater than the value at the root. An important property of the binary search tree is that **the inorder traversal of a BST gives us the elements in a sorted order**.  

Because of this, an in-order traversal of the nodes will yield all the values in increasing order. 

- Flattening the BST
- Controlled Recursion-Using Stack

### Python


```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class BSTIterator:
#     def __init__(self, root: TreeNode):
#         '''Flattening the BST'''
#         self.sorted_nodes = []
#         self.index = -1
#         self._inorder(root)
        
#     def _inorder(self, root):
#         if not root: return
#         self._inorder(root.left)
#         self.sorted_nodes.append(root.val)
#         self._inorder(root.right)            
        

#     def next(self) -> int:
#         """
#         @return the next smallest number
#         """
#         self.index += 1
#         return self.sorted_nodes[self.index]


#     def hasNext(self) -> bool:
#         """
#         @return whether we have a next smallest number
#         """
#         return self.index + 1 < len(self.sorted_nodes)



    def __init__(self, root: TreeNode):
        '''Controlled Recursion-Using Stack'''
        self.stack = []
        while root != None:
            self.stack.append(root)
            root = root.left
            

    def next(self) -> int:
        """
        @return the next smallest number
        """
        topmost_node = self.stack.pop()
        node = topmost_node.right
        while node:
            self.stack.append(node)
            node = node.left
        return topmost_node.val

    def hasNext(self) -> bool:
        """
        @return whether we have a next smallest number
        """        
        return bool(self.stack)
        # return len(self.stack) > 0


# Your BSTIterator object will be instantiated and called as such:
# obj = BSTIterator(root)
# param_1 = obj.next()
# param_2 = obj.hasNext()
```
