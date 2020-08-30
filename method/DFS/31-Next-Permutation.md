- DFS

### Python
```python
class Solution:
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        '''DFS'''
        n = len(nums)
        if n <= 1: return
        i = n - 1
        while i > 0 and nums[i] <= nums[i - 1]:
            i -= 1
        if i != 0:
            j = n - 1
            while nums[j] <= nums[i - 1]:
                j -= 1
            nums[j], nums[i - 1] = nums[i - 1], nums[j]
        self.swapList(nums, i, n - 1)

    # 用于翻转nums[i]到nums[j]，包含两端的这一小段数组
    def swapList(self, nums, i, j):
        while i < j:
            nums[i], nums[j] = nums[j], nums[i]
            i += 1
            j -= 1
```

### Java
```java
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A list of integers that's next permuation
    */
    // 用于交换nums[i]和nums[j]
    public void swapItem(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    // 用于翻转nums[i]到nums[j]，包含两端的这一小段数组
    public void swapList(int[] nums, int i, int j) {
        while (i < j) {
            swapItem(nums, i, j);
            i ++; 
            j --;
        }
    }
    public void nextPermutation(int[] nums) {
        int len = nums.length;
        if ( len <= 1) {
            return;
        }
        int i = len - 1;
        while (i > 0 && nums[i] <= nums[i - 1]) {
            i --;
        }
        if (i != 0) {
            int j = len - 1;
            while (nums[j] <= nums[i - 1]) {
                j--;
            }
            swapItem(nums, j, i-1);
        }
        swapList(nums, i, len - 1);
    }
}
```
### 一些可以做得更细致的地方：
> - 为了确定何时结束，建议在迭代前，先对输入nums数组进行升序排序，迭代到降序时，就都找完了。
> - 在 nextPermutation 当中，当且仅当数组完全降序，那么从右往左遍历的指针 i 最终会指向 0 。所以可以为 nextPermutation 带上布尔返回值，当 i 为 0 时，返回 false，表示找完了。要注意，排序操作在这样一个 NP 问题中，消耗的时间几乎可以忽略。
> - 当数组长度为 1 时，nextPermutation 会直接返回 false ；当数组长度为 0 时， nextPermutation 中 i 会成为 -1 ，所以返回 false 的条件可以再加上 i 为 -1 。
> - Java中，如果输入类型是 int[] ，而输出类型是 List<List> ，要注意，并没有太好的方法进行类型转换，这是由于 int 是基本类型。建议还是自行手动复制，实际工作中还可使用 guava 库。
### Java 
```java
public class Solution {
    /*
     * @param nums: A list of integers.
     * @return: A list of permutations.
     */
    public List<List<Integer>> permute(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        
        boolean next = true;  // next 为 true 时，表示可以继续迭代
        while (next)  {
            List<Integer> current = new ArrayList<>();  // 进行数组复制
            for (int num : nums) {
                current.add(num);
            }
            
            result.add(current);
            next = nextPermutation(nums);
        }
        return result;
    }
    // 用于交换nums[i]和nums[j]
    public void swapItem(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    // 用于翻转nums[i]到nums[j]，包含两端的这一小段数组
    public void swapList(int[] nums, int i, int j) {
        while (i < j) {
            swapItem(nums, i, j);
            i ++; 
            j --;
        }
    }
    public boolean nextPermutation(int[] nums) {
        int len = nums.length;
        int i = len - 1;
        while (i > 0 && nums[i] <= nums[i - 1]) {
            i--;
        }
        if (i <= 0) {
            return false;
        }
        
        int j = len - 1;
        while (nums[j] <= nums[i - 1]) {
            j--;
        }
        swapItem(nums, j, i - 1);
        
        swapList(nums, i, len - 1);
        
        return true;
    }
    
}
```

### Python
```python
class Solution:
    """
    @param: nums: A list of integers.
    @return: A list of permutations.
    """
    def permute(self, nums):
        # write your code here
        nums.sort()
        result = []


        hasNext = True  # hasNext 为 true 时，表示可以继续迭代
        while hasNext:
            current = list(nums)  # 进行数组复制
            result.append(current)
            hasNext = self.nextPermutation(nums)
        
        return result


    def swapList(self, nums, i, j):
        while i < j:
            nums[i], nums[j] = nums[j], nums[i]
            i += 1
            j -= 1
            
    def nextPermutation(self, nums):
        n = len(nums)
        if n <= 1:
            return
        
        i = n - 1
        while i > 0 and nums[i] <= nums[i-1]:
            i -= 1


        if i <= 0:
            return False


        j = n-1
        while nums[j] <= nums[i-1]:
            j -= 1
        nums[j], nums[i-1] = nums[i-1], nums[j]
        
        self.swapList(nums, i, n-1)


        return True
```