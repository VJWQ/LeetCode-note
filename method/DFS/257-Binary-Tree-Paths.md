- Recursion(DFS)
- Iteration(BFS)

### Python

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def binaryTreePaths(self, root: TreeNode) -> List[str]:
        '''Recursive-1'''
        # if not root: return []
        # if not root.left and not root.right:
        #     return [str(root.val)]
        # paths = list()
        # if root.left:
        #     for i in self.binaryTreePaths(root.left):
        #         paths.append(str(root.val) + '->' + i)
        # if root.right:
        #     for i in self.binaryTreePaths(root.right):
        #         paths.append(str(root.val) + '->' + i)
        # return paths


        '''Recursive-2'''
        def construct_paths(root, path):
            if root:
                path += str(root.val)
                if not root.left and not root.right:  # if reach a leaf
                    paths.append(path)  # update paths  
                else:
                    path += '->'  # extend the current path
                    construct_paths(root.left, path)
                    construct_paths(root.right, path)

        paths = []
        construct_paths(root, '')
        return paths


        '''Iterative'''
        # if not root:
        #     return []
        
        # paths = []
        # stack = [(root, str(root.val))]
        # while stack:
        #     node, path = stack.pop()
        #     if not node.left and not node.right:
        #         paths.append(path)
        #     if node.left:
        #         stack.append((node.left, path + '->' + str(node.left.val)))
        #     if node.right:
        #         stack.append((node.right, path + '->' + str(node.right.val)))
        
        # return paths
```
