https://leetcode.com/problems/search-insert-position/

### Python
```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        while left <= right:
            pivot = (left + right) // 2
            if nums[pivot] == target:
                return pivot
            elif nums[pivot] < target:
                left = pivot + 1
            else:
                right = pivot -1
        return left
```
### Java
```Java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int pivot, left = 0, right = nums.length - 1;
        while(left <= right) {
            pivot = (left + right) / 2;
            if(nums[pivot] == target) return pivot;
            if(nums[pivot] < target) left = pivot + 1;
            else right = pivot - 1;
        }
        return left;
    }
}
```
