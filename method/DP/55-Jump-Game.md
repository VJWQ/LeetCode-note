- Greedy
- DP

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
