https://leetcode.com/problems/find-pivot-index/
### Python
```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        res = sum(nums)
        leftsum = 0
        
        for i, value in enumerate(nums):
            if leftsum * 2 + value == res:
                return i
            leftsum += value
        return -1
    
        # for i in range(len(nums)):
        #     if leftsum * 2 + nums[i] == res:
        #         return i
        #     leftsum += nums[i]
        # return -1
```

### Java
```Java
class Solution {
    public int pivotIndex(int[] nums) {
        int res = 0, leftsum = 0;
        for(int num:nums) res += num;
        for(int i = 0; i < nums.length; i++){
            if(leftsum+leftsum+nums[i] == res)
                return i;
            leftsum += nums[i];
        }
        return -1;
    }
}
```
