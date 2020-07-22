- Three Pointers

### Python

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        '''Three Pointers'''
        left, right, cur = 0, len(nums) - 1, 0
        while cur <= right:
            if nums[cur] == 2:
                nums[right], nums[cur] = nums[cur], nums[right]
                right -= 1
            elif nums[cur] == 0:
                nums[left], nums[cur] = nums[cur], nums[left]
                left += 1
                cur += 1
            else:
                cur += 1
```
