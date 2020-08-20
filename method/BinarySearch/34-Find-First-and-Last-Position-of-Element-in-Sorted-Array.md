# First Position of Target
```python
    def binarySearch(self, nums, target):
        if len(nums) == 0: return -1
        start, end = 0, len(nums) - 1
        while start + 1 < end:
            mid = (start + end) // 2

            if nums[mid] == target:
                end = mid
            elif nums[mid] < target:
                start = mid + 1
            else:
                end = mid - 1
                
        if nums[start] == target:
            return start
            
        if nums[end] == target:
            return end
            
        return -1
```


# Last Position of Target
```python
    def lastPosition(self, nums, target):
        if len(nums) == 0: return -1
        start, end = 0, len(nums) - 1
        while start + 1 < end:
            mid = (start + end) // 2

            if nums[mid] == target:
                start = mid
            elif nums[mid] < target:
                start = mid + 1
            else:
                end = mid - 1
                
        if nums[end] == target:
            return end
            
        if nums[start] == target:
            return start
            
        return -1
```

# First and Last Position of Element in Sorted Array
```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        '''Binary Search-1'''
    #     return [self.left_bound(nums,target), self.right_bound(nums,target)]
        
    # def right_bound(self, nums, target):
    #     if len(nums) == 0:
    #         return -1
    #     left, right = 0, len(nums) - 1
    #     while left <= right:
    #         mid = (left + right) // 2
    #         if nums[mid] == target:
    #             left = mid + 1
    #         elif nums[mid] < target:
    #             left = mid + 1
    #         elif nums[mid] > target:
    #             right = mid - 1
    #     if right >= 0 and nums[right] == target: return right # 注意
    #     else: return -1
    # def left_bound(self, nums, target):
    #     if len(nums) == 0:
    #         return -1
    #     left, right = 0, len(nums) - 1

    #     while left <= right:
    #         mid = (left + right) // 2
    #         if nums[mid] == target:
    #             right = mid - 1
    #         elif nums[mid] < target:
    #             left = mid + 1
    #         elif nums[mid] > target:
    #             right = mid - 1
    #     if left <= len(nums)-1 and nums[left] == target: return left  # 注意
    #     else: return -1  

        '''Binary Search-2'''   
        if not nums:
            return [-1, -1]
        
        left, right = -1, -1
        start, end = 0, len(nums) - 1 
        while start + 1 < end:
            mid = (start + end) // 2 
            if nums[mid] <= target:
                start = mid
            else:
                end = mid
        if nums[start] == target:
            right = start
        if nums[end] == target:
            right = end
        
        start, end = 0, len(nums) - 1 
        while start + 1 < end:
            mid = (start + end) // 2 
            if nums[mid] >= target:
                end = mid
            else:
                start = mid
        if nums[end] == target:
            left = end
        if nums[start] == target:
            left = start
        if left == -1 and right == -1:
            return [-1, -1]
        return [left, right]  
```

