# 104. Maximum Depth of Binary Tree

## DFS + DC + Recursive
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0
        else:
            return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```
##  DFS + Stack + Iterative
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

## BFS + Queue + Incursive
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0 # 树为空，返回0
        max_depth = 0 # 最大深度初始化为0
        queue = [root]

        while queue:
            current_level_size = len(queue) # 当前层次的节点个数
            for _ in range(current_level_size): 
                # 弹出当前层次的所有节点，并将每个节点的孩子节点入队
                node = queue.pop(0)
                if node.left: queue.append(node.left)
                if node.right: queue.append(node.right)
            max_depth += 1 # 每遍历完一层的节点，max_depth+1

        return max_depth
        
        # if not root: return 0
        # queue = [(1, root)]
        # while queue:
        #     print(queue)
        #     cur_dep, node = queue.pop(0)
        #     if node.left:
        #         queue.append((cur_dep+1,node.left))
        #     if node.right:
        #         queue.append((cur_dep+1,node.right))
        #     print("***********")
        # return cur_dep
```


        


