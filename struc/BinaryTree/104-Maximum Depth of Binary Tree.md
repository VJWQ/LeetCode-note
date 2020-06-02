# 104. Maximum Depth of Binary Tree
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
```
##  DFS + Stack + Iterative: from top to bottom
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0
        stack = [(1, root),] # Only containing root; depth = 1
        max_depth = float('-inf')
        while stack:
            depth, node = stack.pop()
            if not node.left and not node.right: # 遇到当前节点为叶子节点时，更新最大深度
                max_depth = max(depth, max_depth) # 只保留其中最大的深度
            if node.left: # 若存在左孩子，则压入栈，深度+1
                stack.append((depth + 1, node.left))
            if node.right: # 若存在右孩子，则压入栈，深度+1
                stack.append((depth + 1, node.right))
        return max_depth
    
```

## BFS + Queue + Iterative: from top to bottom
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0   # Empty tree; return 0
        queue = [root]
        depth = 0
        while queue:
            for _ in range(len(queue)): # For each element in the current level
                # 弹出当前层次的所有节点，并将每个节点的孩子节点入队
                node = queue.pop(0)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            depth += 1  # depth + 1 when finish nodes on the current level
        return depth
```

## DFS + DC + Recursive: 
“自顶向下”的“顶”在树中表现为根结点，“自顶向下”指的就是从根结点向下走。  
“自底向上”的“底”在树中表现为叶结点，“自底向上”指的就是从叶结点向上走。
### From bottom to top
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0
        else:
            return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```
### From top to bottom
```python
class Solution:
        def top_down(node, h):
            if not node: return h
            else:
                return max(top_down(node.left, h + 1), top_down(node.right, h + 1))
        return top_down(root, 0)
```

        


