- Brute Force
- Hashset/Hashmap
- Sort + Two pointers  
[A solution notes from Stanford](https://web.stanford.edu/class/cs9/sample_probs/TwoSum.pdf)

### Python

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        '''Brute Force'''
        # for i in nums:
        #     rest = target - i
        #     muns = nums[nums.index(i)+1:]
        #     if rest in muns:
        #         return nums.index(i), muns.index(rest)+len(nums)-len(muns)

        '''hashset/hashmap'''
        # hashmap = {}
        # for index, num in enumerate(nums):
        #     if target - num in hashmap:
        #         return [hashmap[target - num], index]
        #     hashmap[num] = index
        # return None

        '''Sort + Two Pointers-1'''
        # array = nums.copy()
        # nums.sort()

        # left, right = 0, len(nums) - 1
        # while left < right:
        #     if nums[left] + nums[right] > target:
        #         right -= 1
        #     elif nums[left] + nums[right] < target:
        #         left += 1
        #     else:
        #         if nums[left] == nums[right]:
        #             return [i for i, val in enumerate(array) if val == nums[left]]
        #         else:
        #             return array.index(nums[left]), array.index(nums[right])

        # return [-1, -1]

        '''Sort + Two Pointers-2'''
        if not nums:
            return [-1, -1]
        array = [
            (value, index) for index, value in enumerate(nums)
        ]

        array.sort()
        left, right = 0, len(nums) - 1

        while left < right:
            if array[left][0] + array[right][0] > target:
                right -= 1
            elif array[left][0] + array[right][0] < target:
                left += 1
            else:
                return sorted([array[left][1], array[right][1]])

        return [-1, -1]
```
