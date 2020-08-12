### Python
```python
class Solution:
    """
    @param A: an integer array
    @param V: an integer array
    @param m: An integer
    @return: an array
    """
    def backPackIII(self, A, V, m):
        # write your code here
        dp = [0] * (m + 1)
        for i in range(len(A)):
            # 滚动数组优化 正序枚举j
            for j in range(A[i], m + 1):
                dp[j] = max(dp[j], dp[j - A[i]] + V[i])
                
        return dp[m]
```
