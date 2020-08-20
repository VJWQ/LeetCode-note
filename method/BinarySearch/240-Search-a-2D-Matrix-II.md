Similar with the problem [LintCode 38. Search a 2D Matrix II](#LintCode-38) 
- Binary Search

### Python

```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        '''Binary Search'''
        # if matrix == None or len(matrix) == 0:
        #     return False
        
        # n, m = len(matrix), len(matrix[0])
        # x, y = 0, m-1
        # while x <= n - 1 and y >= 0:
        #     goal = matrix[x][y]
        #     if target > goal:
        #         x += 1
        #     if target < goal:
        #         y -= 1
        #     if target == goal:
        #         return True
        # return False

        if matrix == None or len(matrix) == 0:
            return False
        n, m = len(matrix),len(matrix[0])
        # if n == 0 or m==0:
            # return False
        #从左下角往右上角走，(x,y)=(n-1,0)
        x,y = n-1,0
        while x >= 0 and y < m:
            #如果matrix[x][y]等于target，则找到一个相等的值，由于严格排序，直接跳到右上角继续搜
            if matrix[x][y] == target:
                # ans += 1;
                # x -= 1
                # y += 1
                return True
            #如果matrix[x][y]比target大，则往上走
            elif matrix[x][y] > target:
                x -= 1
            #如果matrix[x][y]比target小，则往右走
            else:
                y += 1
        return False
```

## [LintCode 38](https://www.lintcode.com/problem/search-a-2d-matrix-ii/description)
```python
class Solution:
    """
    @param matrix: A list of lists of integers
    @param target: An integer you want to search in matrix
    @return: An integer indicate the total occurrence of target in the given matrix
    """
    def searchMatrix(self, matrix, target):
        count = 0
        if not matrix or len(matrix) == 0 or len(matrix[0]) == 0:
            return 0
        x, y = len(matrix) - 1, 0
        while x >= 0 and y < len(matrix[0]):
            if matrix[x][y] == target:
                x -= 1
                y += 1  # Because [x-1][y] must < [x][y]
                count += 1
            elif matrix[x][y] > target:
                x -= 1
            else:
                y += 1
        
        return count
```
