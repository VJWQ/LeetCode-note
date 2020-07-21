- Two Pointers  
- Add and Sort  

### Python 

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        '''Two Pointers'''
        # if m == 0: nums1[0] = nums2[0]

        # i, j, p = m - 1, n - 1, m + n - 1
        
        # while i >= 0 and j >= 0:
        #     if nums1[i] >= nums2[j]:
        #         nums1[p] = nums1[i]
        #         i -= 1
        #     else:
        #         nums1[p] = nums2[j]
        #         j -= 1
        #     p -= 1
            
        # while j >= 0:
        #     nums1[p] = nums2[j]
        #     j -= 1
        #     p -= 1

        '''Add and Sort'''
        for i in range(n):
            nums1[i + m] = nums2[i]
            
        nums1.sort()
        return nums1
```
