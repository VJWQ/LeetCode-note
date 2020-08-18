- Python: use set()
- Two pointers: with the same direction.  


### Python
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        '''Use set()'''
        a = set(nums)  # 变成集合
        nums.clear()  # 清空列表
        a = list(a)  # 集合变列表
        nums.extend(a)  # 将集合添加到列表
        nums.sort()
        return len(nums) 
        
        
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
        # if not nums: return 0
        # n = len(nums)
        # # nums.sort()
        # j = 1 
        # for i in range(n):
        #     while j < n and nums[j] == nums[i]:
        #         j += 1 
        #     if j >= n:
        #         break
        #     nums[i + 1] = nums[j]
        # return i + 1
```
