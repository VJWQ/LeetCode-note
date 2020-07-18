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
        #     another_num = target - num
        #     if another_num in hashmap:
        #         return [hashmap[another_num], index]
        #     hashmap[num] = index
        # return None

        '''Sort + Two Pointers'''
        array = nums.copy()
        nums.sort()

        left, right = 0, len(nums) - 1
        while left < right:
            if nums[left] + nums[right] > target:
                right -= 1
            elif nums[left] + nums[right] < target:
                left += 1
            else:
                if nums[left] == nums[right]:
                    return [i for i, val in enumerate(array) if val == nums[left]]
                else:
                    return array.index(nums[left]), array.index(nums[right])

        return [-1, -1]
```
