- Iteration
- Recursive
- Notice the difference between **.append(i)** and **.extend(i)**  

### Python

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        '''Iteration'''
        # if not root:
        #     return []

        # stack, res = [root], []

        # while stack:
        #     cur = stack.pop()
        #     if cur:
        #         res.append(cur.val)
        #         if cur.right:
        #             stack.append(cur.right)
        #         if cur.left:
        #             stack.append(cur.left)

        # return res

        '''Recursive-1'''
        # if not root:
        #     return []
            
        # res = []
        
        # def rec(node):
        #     if node:
        #         res.append(node.val)
        #         rec(node.left)
        #         rec(node.right)
        
        # rec(root)
        
        # return res
        

        '''Recursive-2'''
        if not root:
            return []

        res = [root.val]
        res.extend(self.preorderTraversal(root.left))
        res.extend(self.preorderTraversal(root.right))

        return res

        '''Recursive-3'''
        if not root:
            return []
            
        return [root.val] + self.preorderTraversal(root.left) + self.preorderTraversal(root.right)
```
