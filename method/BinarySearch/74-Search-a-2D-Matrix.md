- Binary Search

### Python
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        '''Binary Search'''
    #     if not matrix or not matrix[0]: return False
    #     n, m = len(matrix), len(matrix[0])
    #     start, end = 0, n * m - 1
    #     while start + 1 < end:
    #         mid = (start + end) // 2
    #         if self.get(matrix, mid) < target:
    #             start = mid
    #         else:
    #             end = mid

    #     if self.get(matrix, start) == target:
    #         return True
    #     if self.get(matrix, end) == target:
    #         return True
    #     return False
    
    # def get(self, matrix, index):
    #     x = index // len(matrix[0])
    #     y = index % len(matrix[0])
    #     return matrix[x][y]


        if matrix == None or len(matrix) == 0:
            return False
        
        n, m = len(matrix), len(matrix[0])
        x, y = 0, m-1
        while x <= n - 1 and y >= 0:
            goal = matrix[x][y]
            if target > goal:
                x += 1
            if target < goal:
                y -= 1
            if target == goal:
                return True
        return False
```
