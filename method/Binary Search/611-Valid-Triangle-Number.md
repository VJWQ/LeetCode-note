- Brute Force
- Two Pointers
- Binary Search

### Python
```python
class Solution:
    def triangleNumber(self, nums: List[int]) -> int:
        '''Brute Force-1'''
        # n = len(nums)
        # ans = 0
        # for i in range(n - 2):
        #     for j in range(i + 1, n - 1):
        #         for k in range(j + 1, n):
        #             if nums[i] + nums[j] > nums[k] and nums[i] + nums[k] > nums[j] and nums[j] + nums[k] > nums[i]: ans += 1

        # return ans

        '''Brute Force-2'''
        # n = len(nums)
        # ans = 0
        # nums.sort()
        # for i in range(n - 2):
        #     if nums[i] == 0: continue
        #     k = i + 2
        #     for j in range(i + 1, n - 1):
        #         while k < n and nums[i] + nums[j] > nums[k]:
        #             k += 1
        #         ans += k - j - 1
        # return ans

        '''Two Pointers'''
        # nums.sort()
        # count = 0
        # for i in range(len(nums)):
        #     left, right = 0, i - 1
        #     while left < right:
        #         if nums[left] + nums[right] > nums[i]:
        #             count += right - left
        #             right -= 1
        #         else:
        #             left += 1
        # return count


        '''Binary Search'''
        
```
