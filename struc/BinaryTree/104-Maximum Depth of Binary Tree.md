# 104. Maximum Depth of Binary Tree

## Recursive + DFS

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0
        if root:
            return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```
## Incursive + DFS

## Incursive + BFS

