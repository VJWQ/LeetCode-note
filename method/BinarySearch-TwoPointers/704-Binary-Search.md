- Recursive
- Non-Recursive

### Python

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        '''Recursive'''
    #     return self.binary_search(nums, 0, len(nums) - 1, target)
    
    # def binary_search(self, nums, start, end, target):
    #     if start > end: return -1

    #     mid = (start + end) // 2
    #     if nums[mid] == target: return mid
    #     elif nums[mid] < target:
    #         return self.binary_search(nums, mid + 1, end, target)
    #     else:
    #         return self.binary_search(nums, start, mid - 1, target)

        '''Non-Recursive'''
        start, end = 0, len(nums) - 1
        while start <= end:
            mid = (start + end) // 2

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                start = mid + 1
            else:
                end = mid - 1
        return -1
```
