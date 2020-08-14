

## 92. Backpack I

只有在m>>2^n的时候，动态规划才弱于搜索，所以大部分情况下，动态规划都是一个最优的选择   
- DP
- A Space Optimized DP solution: uses rolling arrays to optimize the space usage. 使用dp[j-A[i]]代替dp[i-1][j-A[i]]。
[填表](https://www.youtube.com/watch?v=UBth-pABHoM)

### Python
```python
class Solution:
    """
    @param m: An integer m denotes the size of a backpack
    @param A: Given n items with size A[i]
    @return: The maximum size
    """
    def backPack(self, m, A):
        '''DP-1: 2D array with boolean'''
        # n = len(A)
        # # state: dp[i][j] represents if the sum of j can be satisifed with the first i numbers
        # dp = [[False] * (m + 1) for _ in range(n + 1)]
        
        # # initialize: from the first 0 nmbers can get the sum of 0
        # dp[0][0] = True
        
        # # function: 
        # for i in range(1, n + 1):
        #     dp[i][0] = True
        #     for j in range(1, m + 1):
        #         if j >= A[i - 1]:
        #             dp[i][j] = dp[i - 1][j] or dp[i - 1][j - A[i - 1]]
        #         else:
        #             dp[i][j] = dp[i - 1][j]
                    
        # # answer
        # for i in range(m, -1, -1):
        #     if dp[n][i]:
        #         return i
        # return 0

        
        '''DP-2: 2D array with value'''
        n = len(A)
        dp = [[0] * (m + 1) for _ in range(n + 1)]
        
        for i in range(1, n + 1):
            for j in range(1, m + 1):
                if j >= A[i - 1]:       # 判断背包容量是不是大于第i件物品的体积
                    # select or not
                    dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - A[i - 1]]+A[i - 1])
                else:
                    dp[i][j] = dp[i - 1][j]

        return dp[-1][-1]
        
        
        '''DP-3: optimized with 1D array'''
        n = len(A)
        f = [[False] * (m + 1), [False] * (m + 1)]
        
        f[0][0] = True
        for i in range(1, n + 1):
            f[i % 2][0] = True
            for j in range(1, m + 1):
                if j >= A[i - 1]:
                    f[i % 2][j] = f[(i - 1) % 2][j] or f[(i - 1) % 2][j - A[i - 1]]
                else:
                    f[i % 2][j] = f[(i - 1) % 2][j]
                    
        for i in range(m, -1, -1):
            if f[n % 2][i]:
                return i
        return 0
        
        
        '''DP-4: optimized with 1D array'''
        # if m == 0 or len(A) == 0:
        #     return 0
        # n = len(A)
        # dp = [0 for _ in range(m + 1)]
        # for i in range(n):
        #     # 滚动数组优化 倒序枚举j
        #     # for j in range(m, A[i] - 1, -1):
        #     for j in range(m, - 1, -1):
        #         dp[j] = max(dp[j], dp[j - A[i]] + A[i])
                
        # return dp[m]
```
## 125. Backpack II
## 440. Backpack III
## 562. Backpack IV
## 563. Backpack V
## 564. Backpack VI
