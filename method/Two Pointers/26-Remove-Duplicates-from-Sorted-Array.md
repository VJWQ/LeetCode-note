Two pointers with the same direction.  

### Python
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        # if not nums: return 0
        # i = 0
        # for j in range(1, len(nums)):
        #     if nums[i] == nums[j]:
        #         j += 1
        #     else:
        #         nums[i+1] = nums[j]
        #         i += 1
        # return i + 1    # return the new length

        '''Two Pointers'''
        if not nums: return 0
        n = len(nums)
        # nums.sort()
        j = 1 
        for i in range(n):
            while j < n and nums[j] == nums[i]:
                j += 1 
            if j >= n:
                break
            nums[i + 1] = nums[j]
        return i + 1
```
