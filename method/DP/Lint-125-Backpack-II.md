### Python

```python
class Solution:
    """
    @param m: An integer m denotes the size of a backpack
    @param A: Given n items with size A[i]
    @param V: Given n items with value V[i]
    @return: The maximum value
    """
    def backPackII(self, m, A, V):
        '''DP-1: 2D array with value'''
        # n = len(A)
        # dp = [[0] * (m + 1), [0] * (m + 1)]
        # for i in range(1, n + 1):
        #     dp[i % 2][0] = 0
        #     for j in range(1, m + 1):
        #         dp[i % 2][j] = dp[(i - 1) % 2][j]
        #         if A[i - 1] <= j:
        #             dp[i % 2][j] = max(dp[(i - 1) % 2][j], dp[(i - 1) % 2][j - A[i - 1]] + V[i - 1])
        # return dp[n % 2][m]
        
        '''DP-2: optimized with 1D array'''
        dp = [0] * (m + 1)
        for i in range(len(A)):
            # 滚动数组优化 倒序枚举j
            for j in range(m, A[i] - 1, -1):
                dp[j] = max(dp[j], dp[j - A[i]] + V[i])
                
        return dp[m]
```
