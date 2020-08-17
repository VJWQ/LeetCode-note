Identical with the problem: [518. Coin Change 2](https://leetcode.com/problems/coin-change-2/)

- DP-1: 2D array
- DP-2: 1D array

### Python
```python
class Solution:
    """
    @param nums: an integer array and all positive numbers, no duplicates
    @param target: An integer
    @return: An integer
    """
    def backPackIV(self, nums, target):
        '''DP-1: 2D array'''
        # if not nums:
        #     return 0
            
        # n = len(nums)
        # dp = [[0] * (target + 1), [0] * (target + 1)]
        # dp[0][0] = 1
        # for i in range(1, n + 1):
        #     dp[i % 2][0] = 1
        #     for j in range(1, target + 1):
        #         dp[i % 2][j] = dp[(i - 1) % 2][j]
        #         if j >= nums[i - 1]:
        #             dp[i % 2][j] += dp[i % 2][j - nums[i - 1]]
        # return dp[n % 2][target]
        
        '''DP-2: 1D array'''
        # 状态dp[s]表示能装满容量为s的背包的最多方案数
        # 使用无限次是正着循环
    	n = len(nums)
    	dp = [0] * (target + 1)
    	dp[0] = 1
    	for i in range(n):
    		for j in range(nums[i], target + 1):
    			dp[j] += dp[j - nums[i]]
    			# if nums[i] == j:
    			# 	dp[j] += 1
    			# elif nums[i] < j:
    			# 	dp[j] += dp[j - nums[i]]

    	return dp[target]
```
