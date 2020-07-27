-Binary Search

### Python

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        '''Binary Search-1'''
        # if len(nums) == 1: return nums[0]
        # left, right = 0, len(nums) - 1
        # while left < right:
        #     mid = (left + right) // 2
        #     if nums[mid] <nums[right]:
        #         right = mid
        #     else:
        #         left = mid + 1
        # return nums[left]

        '''Binary Search-2'''
        if not nums:
            return -1
            
        start, end = 0, len(nums) - 1
        target = nums[-1]
        while start + 1 < end:
            mid = (start + end) // 2
            if nums[mid] <= target:
                end = mid
            else:
                start = mid
        return min(nums[start], nums[end])
```
