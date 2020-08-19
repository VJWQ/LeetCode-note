- Two Pointers

### Python
```python
class Solution:
    """
    @param nums: a list of integers.
    @param k: length of window.
    @return: the sum of the element inside the window at each moving.
    """
    def winSum(self, nums, k):
        '''Two Pointers'''
        if not nums or len(nums) < k:
            return []

        res = []
        j, win_sum, n = 0, 0, len(nums)
        for i in range(n):
            while j < n and j - i < k:
                win_sum += nums[j]
                j += 1 
            if j - i == k:
                res.append(win_sum)
            win_sum -= nums[i]
        return res
```
