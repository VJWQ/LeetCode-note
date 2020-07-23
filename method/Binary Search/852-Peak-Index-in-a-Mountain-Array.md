- Linear Scan
- Binary Search

### Python
```python
class Solution:
    def peakIndexInMountainArray(self, A: List[int]) -> int:
        '''Linear Scan'''
        # for i in range(len(A)):
        #     if A[i] > A[i+1]:
        #         return i

        '''Binary Search'''
        low, high = 0, len(A) - 1
        while low < high:
            mid = (low + high) // 2            
            if A[mid] < A[mid + 1]:
                low = mid + 1
            else:
                high = mid
        return low
```
