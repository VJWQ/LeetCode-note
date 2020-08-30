### Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def findTarget(self, root: TreeNode, k: int) -> bool:
        if not root: return
        self.res = None
        node_set = set()
        self.inorder(root, k, node_set)
        return self.res
        
    def inorder(self, root, k, node_set):
        if not root: return
        self.inorder(root.left, k, node_set)
        if root.val in node_set:
            self.res = [k - root.val, root.val]
        else:
            node_set.add(k - root.val)
        self.inorder(root.right, k, node_set)
```
