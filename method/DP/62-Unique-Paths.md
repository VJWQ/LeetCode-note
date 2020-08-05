- DP: top to bottom
- DP: bottom to top  

### Python
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        '''DP: top to bottom'''
        # # state dp[i][j]: total paths from (0, 0) to (i, j)
        # dp = [[0] * n for _ in range(m)]

        # # initialize: column 0 and row 0
        # for i in range(m):
        #     dp[i][0] = 1
        # for j in range(n):
        #     dp[0][j] = 1

        # # function: dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        # for i in range(1, m):
        #     for j in range(1, n):
        #         dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        
        # # answer
        # return dp[m - 1][n - 1]


        '''DP: bottom to top'''
        # state dp[i][j]: total paths from (0, 0) to (i, j)
        dp = [[0] * n for _ in range(m)]

        # initialize: column n - 1 and row m - 1
        for i in range(m):
            dp[i][n - 1] = 1
        for j in range(n):
            dp[m - 1][j] = 1

        # function: dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        for i in range(m - 2, -1, -1):
            for j in range(n - 2, -1, -1):
                dp[i][j] = dp[i + 1][j] + dp[i][j + 1]
        
        # answer
        return dp[0][0]
```
