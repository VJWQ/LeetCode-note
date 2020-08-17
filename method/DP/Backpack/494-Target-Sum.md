
[solution](https://zhuanlan.zhihu.com/p/93857890)  
假设所有元素和为`sum`，所有添加正号的元素的和为`A`，所有添加负号的元素和为`B`，则有`sum = A + B` 且 `S = A - B`，解方程得`A = (sum + S)/2`。
即题目转换成：从数组中选取一些元素使和恰好为`(sum + S) / 2`。可见这是一个**恰好装满的01背包问题，要求所有方案数**。需要注意的是，虽然这里是恰好装满，但是dp初始值不应该是inf，因为这里求的不是总价值而是方案数，应该全部初始为0（除了dp[0]初始化为1）。

### Python
```python
class Solution:
    def findTargetSumWays(self, nums: List[int], S: int) -> int:
        '''DP'''
        if sum(nums) < S: return 0
        if (sum(nums) + S) % 2: return 0
        n = len(nums)
        target = (sum(nums) + S) // 2
        dp = [0] * (target + 1)
        dp[0] = 1
        for i in range(n):
            for j in range(target, nums[i] - 1, -1):
                dp[j] += dp[j - nums[i]]        
        return dp[target]
```
