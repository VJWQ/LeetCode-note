Similar with [Backpack-V](https://github.com/VJWQ/LeetCode-note/blob/master/method/DP/Backpack/Lint-563-Backpack-V.md).   
[Backpack-IV](https://github.com/VJWQ/LeetCode-note/blob/master/method/DP/Backpack/Lint-562-Backpack-IV.md) is identical with [518. Coin Change 2](https://leetcode.com/problems/coin-change-2/).  
## / 和 //的区别
- python中**除号**用`/`表示，得到的值总是**浮点数**，例如：`5 / 5`结果是`1.0`。
- python中**整除**用`//`表示，`//`表示两数相除，向下取整，例如`8 // 5` 结果是`1`。
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
