### Python
```python
class Solution:
    """
    @param nums: an integer array and all positive numbers
    @param target: An integer
    @return: An integer
    """
    def backPackV(self, nums, target):
    	n = len(nums)
    	dp = [0] * (target + 1)
    	dp[0] = 1
    	for i in range(n): 
    		for j in range(target, nums[i] - 1, -1):
    			if j >= nums[i]:
    				dp[j] += dp[j - nums[i]]
    	return dp[target]
```
