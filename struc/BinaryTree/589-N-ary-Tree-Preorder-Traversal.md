- Iteration
- Recursive

### Python
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        '''Iteration'''
        if not root:
            return []
                
        stack, res = [root], []

        while stack:
            cur = stack.pop()
            if cur:
                res.append(cur.val)
                for kid in cur.children[::-1]:
                    stack.append(kid)
                # stack.extend(cur.children[::-1])

        return res

        '''Recursive'''
        # if not root:
        #     return []

        # res = [root.val]

        # if root.children:
        #     for kid in root.children:
        #         res.extend(self.preorder(kid))
                
        # return res
```
