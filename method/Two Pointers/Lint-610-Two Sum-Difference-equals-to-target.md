### Python
```python
class Solution:
    """
    @param nums: an array of Integer
    @param target: an integer
    @return: [num1, num2] (num1 < num2)
    """
    def twoSum7(self, nums, target):
        n = len(nums)
        if target < 0:
            target = -target
        # 这里如果我们不将target置为其绝对值，会出现无法获得target的情况。
        # 因为我们的双指针移动过程中判断的都nums[j] - nums[i] 是否等于target。
        # 而如果j > i，那么nums[j] >= nums[i]，nums[j] - nums[i] 一定不与target相等，因此会找不到解。
        j = 0
        for i in range(n):
            if i == j:
                j += 1
            while j < n and nums[j] - nums[i] < target:
                j += 1
            if j < n and nums[j] - nums[i] == target:
                return [nums[i],nums[j]]
```
