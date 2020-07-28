### Python

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
from collections import deque

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        '''BFS-Single Queue'''
        # if root is None: return []
        # queue = deque([root])
        # res = list()

        # while queue:
        #     level = list()
        #     for _ in range(len(queue)):
        #         node = queue.popleft()
        #         level.append(node.val)
        #         if node.left:
        #             queue.append(node.left)
        #         if node.right:
        #             queue.append(node.right)
        #     res.append(level)
        # return res

        '''BFS-Double Queue'''
        # if not root: return []
        # queue = [root]
        # res = list()
        # while queue:
        #     next_queue = list()
        #     res.append([node.val for node in queue])
        #     for node in queue:
        #         if node.left:
        #             next_queue.append(node.left)
        #         if node.right:
        #             next_queue.append(node.right)
        #     queue = next_queue
        # return res

        '''DummyNode'''
        if not root: return []
        queue = collections.deque([root, None])
        res, level = [], []
        while queue:
            node = queue.popleft()
            if node is None:
                res.append(level)
                level = []
                if queue:
                    queue.append(None)
                continue
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        return res
```
