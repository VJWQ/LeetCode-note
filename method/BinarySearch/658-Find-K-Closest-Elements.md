- Heap
- Two Pointers
- Binary Search

### Python

```python
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        '''Heap'''
        # heap = list()
        # for i in range(len(arr)):
        #     if len(heap) < k:
        #         heap.append(arr[i])
        #     else:
        #         if abs(arr[i] - x) < abs(heap[0] - x):
        #             heap.pop(0)
        #             heap.append(arr[i])
        # return heap

        '''Two Pointers'''
        # left, right = 0, len(arr) - 1
        # res = list()
        # count = len(arr) - k
        # while count:
        #     if abs(arr[left] - x) <= abs(arr[right] - x):
        #         right -= 1
        #     else:
        #         left += 1
        #     count -= 1
        # return arr[left:left + k]
            
        '''Binary Search'''
        left, right = 0, len(arr) - k

        while left < right:
            mid = left + (right - left) // 2
            if abs(arr[mid] - x) > abs(arr[mid + k] - x):
                left = mid + 1
            else:
                right = mid
        return arr[left:left + k]
```
