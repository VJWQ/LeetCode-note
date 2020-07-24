- Merge and sort 
- Two Pointers: 
  - Two pointers: Start from the beginning
  - Two pointers: Start from the end

### Python 

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        '''Merge and sort-1'''
        # nums1[:] = sorted(nums1[:m] + nums2)


        '''Merge and sort-2'''
        # for i in range(n):
        #     nums1[i + m] = nums2[i]
            
        # nums1.sort()
        # return nums1


        '''Two pointers: Start from the beginning'''
        # Make a copy of nums1.
        nums1_copy = nums1[:m] 
        nums1[:] = []

        # Two get pointers for nums1_copy and nums2.
        p1, p2 = 0, 0
        
        # Compare elements from nums1_copy and nums2:
        # add the smallest one into nums1.
        while p1 < m and p2 < n: 
            if nums1_copy[p1] < nums2[p2]: 
                nums1.append(nums1_copy[p1])
                p1 += 1
            else:
                nums1.append(nums2[p2])
                p2 += 1

        # there are still elements to add
        if p1 < m: 
            nums1[p1 + p2:] = nums1_copy[p1:]
        if p2 < n:
            nums1[p1 + p2:] = nums2[p2:]

        '''Two pointers: Start from the end-1'''
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
        
        # '''Two pointers: Start from the end-2'''
        # p1 = m - 1
        # p2 = n - 1
        # p = m + n - 1
        
        # while p1 >= 0 and p2 >= 0:
        #     if nums1[p1] < nums2[p2]:
        #         nums1[p] = nums2[p2]
        #         p2 -= 1
        #     else:
        #         nums1[p] =  nums1[p1]
        #         p1 -= 1
        #     p -= 1
        
        # # add missing elements from nums2
        # nums1[:p2 + 1] = nums2[:p2 + 1]
```
