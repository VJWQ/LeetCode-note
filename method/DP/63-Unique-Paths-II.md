- DP

### Python
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        '''DP'''
        if not obstacleGrid or not obstacleGrid[0]:
            return 0

        n, m = len(obstacleGrid), len(obstacleGrid[0])

        # state: dp[i][j] represents paths from (0, 0) to (i, j)
        dp = [[0] * m for _ in range(n)]

        # initialize: set to 1 
        for i in range(n):
            if obstacleGrid[i][0]:  # occurs first obstacle on the left border
                break               # ignore the position with obstacle and all later positions
            dp[i][0] = 1            # e.g. [1 1 1 0 0]^T
        for j in range(m):
            if obstacleGrid[0][j]:  # occurs first obstacle on the upper border
                break               # ignore the position with obstacle and all later positions
            dp[0][j] = 1            # e.g. 1 1 0 0 0 

        # function
        for i in range(1, n):
            for j in range(1, m):
                if obstacleGrid[i][j]:  # occurs an obstacle
                    continue            # set dp[i][j] to 0 (original value is already 0)
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        return dp[n - 1][m - 1]
```
