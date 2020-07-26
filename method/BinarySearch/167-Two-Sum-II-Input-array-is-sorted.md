- Two Pointers
- Binary Search

### Python

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        '''Two Pointers-1'''
        # left, right = 0, len(numbers) - 1
        # while left < right:
        #     if numbers[left] + numbers[right] > target:
        #         right -= 1
        #     elif numbers[left] + numbers[right] < target:
        #         left += 1
        #     else:
        #         if numbers[left] == numbers[right]:
        #             return [i + 1 for i, val in enumerate(numbers) if val == numbers[left]]
        #         else:
        #             return numbers.index(numbers[left]) + 1, numbers.index(numbers[right]) + 1

        # return [-1, -1]

        '''Two Pointers-2'''
        # low, high = 0, len(numbers) - 1
        # while low < high:
        #     total = numbers[low] + numbers[high]
        #     if total == target:
        #         return [low + 1, high + 1]
        #     elif total < target:
        #         low += 1
        #     else:
        #         high -= 1

        # return [-1, -1]

        '''Binary Search'''
        for i in range(len(numbers)):
            left, right = i + 1, len(numbers) - 1
            while left <= right:
                mid = (left + right) // 2
                if numbers[mid] == target - numbers[i]:
                    return [i + 1, mid + 1]
                elif numbers[mid] > target - numbers[i]:
                    right = mid - 1
                else:
                    left = mid + 1
        return [-1, -1]



```
