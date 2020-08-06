- Greedy
- DP  


【确认条件】 （1）nums[i]代表在这块石头上最远能跳出去的距离，而不是只能跳出这个距离，这两种情况有区别。 （2）处理异常输入。

【解题思路】 （1）确定状态： dp[i]代表是否能跳到这块石头上，所以dp[n - 1]为答案。 （2）转移方程： 对于石头i而言，遍历之前的所有石头j in range(0, i)。如果有任何一块石头j能够做到 dp[j] == True and j + nums[j] >= i，那么dp[i] = True。 （3）初始状态和边界情况： 开始处位置为0，dp[0] = True，其他全为False。 （4）计算顺序： 从dp[1]到dp[n - 1]。

【实现要点】 寻找到任何一个使得dpi = True的情况即可提前跳出内层循环。

【复杂度】 时间复杂度：O(n ^ 2) 空间复杂度：O(n)

### Python
```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        '''Greedy'''
        n, rightmost = len(nums), 0
        for i in range(n):
            if i <= rightmost:
                rightmost = max(rightmost, i + nums[i])
                if rightmost >= n - 1:
                    return True
        return False

        '''DP'''
        # if not nums:
        #     return False
        # n = len(nums)
        # # states: dp[i] represents if can jump to i
        # dp = [False] * n

        # # initialize: stands on position 0
        # dp[0] = True

        # # function
        # for i in range(1, n):
        #     for j in range(i):
        #         if dp[j] and j + nums[j] >= i:
        #             dp[i] = True
        #             break

        # return dp[n - 1]
```
