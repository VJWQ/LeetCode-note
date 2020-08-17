Similar with [Backpack-V](https://github.com/VJWQ/LeetCode-note/blob/master/method/DP/Backpack/Lint-563-Backpack-V.md).   
[Backpack-IV](https://github.com/VJWQ/LeetCode-note/blob/master/method/DP/Backpack/Lint-562-Backpack-IV.md) is identical with [518. Coin Change 2](https://leetcode.com/problems/coin-change-2/).  
### Python
```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        '''DP'''
        if sum(nums) % 2: return False
        target = sum(nums) // 2
        dp = [0] * (target + 1)
        dp[0] = 1
        for i in range(len(nums)):
            for j in range(target, nums[i] - 1, -1):
                dp[j] += dp[j - nums[i]]
        return dp[target]
```
