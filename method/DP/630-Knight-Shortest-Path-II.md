- DP

### Python

```python
DIRECTIONS = [
    (-1, -2),
    (1, -2),
    (-2, -1),
    (2, -1),
    ]

class Solution:
    """
    @param grid: a chessboard included 0 and 1
    @return: the shortest path
    """
    def shortestPath2(self, grid):
        '''DP'''
        if not grid or not grid[0]:
            return -1
        
        n, m = len(grid), len(grid[0])
        
        # state f[i][j]: least steps from (0, 0) to (i, j)
        f = [[float('inf')] * m for _ in range(n)]

        # initialize: start point f[0][0] 
        f[0][0] = 0
        
        # function
        for j in range(m):
            for i in range(n):
                if grid[i][j]:
                    continue
                for delta_x, delta_y in DIRECTIONS:
                    x, y = i + delta_x, j + delta_y
                    if 0 <= x < n and 0 <= y < m:
                        f[i][j] = min(f[i][j], f[x][y] + 1)

        if f[n - 1][m - 1] == float('inf'):
            return -1

        return f[n - 1][m - 1]
```
