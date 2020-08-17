* Backpack related problem
- DP
- BFS
- DFS

### Python
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        '''DP'''
        # n = len(coins)
        # dp = [sys.maxsize] * (amount + 1)
        # dp[0] = 0

        # for i in range(n):
        #     for j in range(coins[i], amount + 1):
        #         dp[j] = min(dp[j], dp[j - coins[i]] + 1)    # A[i]/V[i]/ 1: 体积/价值/单纯计数
        # # if dp[amount] != sys.maxsize:
        # #     return dp[amount]
        # # else:
        # #     return -1
        # return dp[amount] if dp[amount] != sys.maxsize else -1

        '''BFS'''
        # # from collections import deque
        # queue = deque([amount])
        # step = 0
        # visited = set()
        # while queue:
        #     n = len(queue)
        #     for _ in range(n):
        #         tmp = queue.pop()
        #         if tmp == 0:
        #             return step
        #         for coin in coins:
        #             if tmp >= coin and tmp - coin not in visited:
        #                 visited.add(tmp - coin)
        #                 queue.appendleft(tmp - coin)
        #     step += 1
        # return -1

        '''DFS'''
        coins.sort(reverse=True)
        self.res = float("inf")
        
        def dfs(i, num, amount):
            if amount == 0:
                self.res = min(self.res, num)
                return 
            for j in range(i, len(coins)):
                # 剩下的最大值都不够凑出来了
                if (self.res - num) * coins[j] < amount:
                    break
                if coins[j] > amount:
                    continue
                dfs(j, num + 1, amount - coins[j])
                
        for i in range(len(coins)):
            dfs(i, 0, amount)
            
        return self.res if self.res != float("inf") else -1    
```
