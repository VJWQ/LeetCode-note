- Recursive Inorder + Linear search: build inorder traversal and then find the closest element in a sorted array.  
- Iterative Inorder: the closest value is found if the target value is in-between of two inorder array elements `nums[i] <= target < nums[i + 1]`.
- Binary Search: go left if target is smaller than current root value, and go right otherwise. Choose the closest to target value at each step.  

### Python


```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def closestValue(self, root: TreeNode, target: float) -> int:
        '''Recursive Inorder + Linear search'''
        # def inorder(root):
        #     if root:
        #         return inorder(root.left) + [root.val] + inorder(root.right)
        #     else:
        #         return []
        # return min(inorder(root), key = lambda x: abs(target - x))
    
    
        '''Iterative Inorder'''
#         stack, pred = [], float('-inf')
#         while stack or root:
#             while root:
#                 stack.append(root)
#                 root = root.left
#             root = stack.pop()

#             if pred <= target and target < root.val:
#                 return min(pred, root.val, key = lambda x: abs(target - x))
#             pred = root.val
#             root = root.right
#         return pred
    
        '''Binary Search'''
        res = root.val
        while root:
            res = min(res, root.val, key = lambda x: abs(target - x))
            if target < root.val:
                root = root.left
            else:
                root = root.right
        return res
```
