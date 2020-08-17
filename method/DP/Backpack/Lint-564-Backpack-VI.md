## Combination Sum IV
### Python
```python
class Solution:
    """
    @param nums: an integer array and all positive numbers, no duplicates
    @param target: An integer
    @return: An integer
    """
    def backPackVI(self, nums, target):
    	dp = [0] * (target + 1)
    	dp[0] = 1
    	for i in range(target + 1): 
    		for num in nums:
    			if num <= i:
    				dp[i] += dp[i - num]
    	return dp[target]
```
