- Top-down Recursion  
- Bottom-up Recursion  

[A good analysis can be found here](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/solution/mian-shi-ti-55-ii-ping-heng-er-cha-shu-cong-di-zhi/)

### Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    '''Top-down Recursion'''
    # def height(self, root: TreeNode) -> int:
    #     if not root: return -1
    #     return 1 + max(self.height(root.left), self.height(root.right))

    # def isBalanced(self, root: TreeNode) -> bool:
    #     if not root: return True

    #     return abs(self.height(root.left) - self.height(root.right)) < 2 and self.isBalanced(root.left) and self.isBalanced(root.right)

    '''Bottom-up Recursion-1'''
    # # Return whether or not the tree at root is balanced while also returning
    # # the tree's height
    # def isBalancedHelper(self, root: TreeNode) -> (bool, int):
    #     # An empty tree is balanced and has height -1
    #     if not root:
    #         return True, -1
        
    #     # Check subtrees to see if they are balanced. 
    #     leftIsBalanced, leftHeight = self.isBalancedHelper(root.left)
    #     if not leftIsBalanced:
    #         return False, 0
    #     rightIsBalanced, rightHeight = self.isBalancedHelper(root.right)
    #     if not rightIsBalanced:
    #         return False, 0
        
    #     # If the subtrees are balanced, check if the current tree is balanced
    #     # using their height
    #     return (abs(leftHeight - rightHeight) < 2), 1 + max(leftHeight, rightHeight)
        
    # def isBalanced(self, root: TreeNode) -> bool:
    #     return self.isBalancedHelper(root)[0]

    '''Bottom-up Recursion-2'''
    def isBalanced(self, root: TreeNode) -> bool:
        return self.recur(root) != -1
    
    def recur(self, root):
        if not root: return 0
        left = self.recur(root.left)
        if left == -1: return -1
        right = self.recur(root.right)
        if right == -1: return -1
        if abs(left - right) < 2:
            return max(left, right) + 1
        else:
            return -1
```
