- Iteration
- Recursive

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

        '''Recursive'''
        if not root:
            return []
            
        res = []
        
        def rec(node):
            if node:
                res.append(node.val)
                rec(node.left)
                rec(node.right)
        
        rec(root)
        
        return res
        
        # return [root.val] + self.preorderTraversal(root.left) + self.preorderTraversal(root.right)
```
