# [背包九讲](https://anivian.github.io/pack-master/V2.pdf)
# [背包六问](https://segmentfault.com/a/1190000006325321)
[92. Backpack I](https://www.lintcode.com/problem/backpack/description)  
[125. Backpack II](https://www.lintcode.com/problem/backpack-ii/description)  
[440. Backpack III](https://www.lintcode.com/problem/backpack-iii/description)  
[562. Backpack IV](https://www.lintcode.com/problem/backpack-iv/description)  
[563. Backpack V](https://www.lintcode.com/problem/backpack-v/description)  
[564. Backpack VI](https://www.lintcode.com/problem/combination-sum-iv/description)  

1. 单次选择 + 最大体积
2. 单次选择 + 最大价值
3. 重复选择 + 最大价值
4. 重复选择 + 唯一排列 + 装满方案数
5. 单次选择 + 装满方案数
6. 重复选择 + 不同排列 + 装满方案数


## 92. Backpack I
只有在m>>2^n的时候，动态规划才弱于搜索，所以大部分情况下，动态规划都是一个最优的选择   
- DP
- A Space Optimized DP solution: uses rolling arrays to optimize the space usage. 使用dp[j-A[i]]代替dp[i-1][j-A[i]]。

### Python
```python
class Solution:
    """
    @param m: An integer m denotes the size of a backpack
    @param A: Given n items with size A[i]
    @return: The maximum size
    """
    def backPack(self, m, A):
        '''DP-1'''
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

        '''DP-2: with array'''
        n = len(A)
        dp = [0 for x in range(m+1)]
        dp[0] = 1
        ans = 0
        for item in A:
            for i in range(m,-1,-1):
                if i-item >=0 and dp[i-item] > 0:
                    ans = max(ans,i)
                    dp[i] = 1
        return ans
```
## 125. Backpack II
## 440. Backpack III
## 562. Backpack IV
## 563. Backpack V
## 564. Backpack VI
