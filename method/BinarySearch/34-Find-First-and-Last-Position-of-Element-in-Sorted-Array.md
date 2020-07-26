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

