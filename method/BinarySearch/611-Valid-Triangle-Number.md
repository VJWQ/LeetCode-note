- Brute Force
- Two Pointers
- Binary Search
- 降低时间复杂度的主要方法： `空间换时间` 和 `排序换时间`  

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
        nums.sort()

        n = len(nums)
        count = 0
        for i in range(n - 2):
            for j in range(i + 1, n - 1):
                left, right = j + 1, n - 1
                while left < right:
                    mid = (left + right + 1) // 2
                    if nums[mid] < nums[i] + nums[j]:
                        left = mid
                    else: 
                        right = mid - 1 
                if nums[right] < nums[i] + nums[j]:
                    count += right - j
        return count
```
