Binary search is a search algorithm that find the position of a target value within a sorted array.

Time complexity: O(logn). Requires a sorted array.  
普通查找：O(n)。Doesn't ask for sorted array, directly use for-loop.  

在数组中二分，只要是有序数组，就可以进行二分。递增和递减只会与当前位置与目标值的大小关系如何影响边界变化有关。  
同时，二分问题其实并不需要要求数组一定是严格有序的，我们不能根据数组是否有序来判断是否是二分问题。

[Understanding the BS details](https://github.com/labuladong/fucking-algorithm/blob/master/%E7%AE%97%E6%B3%95%E6%80%9D%E7%BB%B4%E7%B3%BB%E5%88%97/%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE%E8%AF%A6%E8%A7%A3.md)

问题类型：
- 在排序的输入集上二分
- 在未排序的输入集上二分
- 二分答案集



## Template:  
### Java:
```java
public class Solution {
    /**
     * @param A an integer array sorted in ascending order
     * @param target an integer
     * @return an integer
     */
    public int findPosition(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return -1;
        }

        int start = 0, end = nums.length - 1;
        // 要点1: start + 1 < end
        while (start + 1 < end) {
     // 要点2：start + (end - start) / 2
            int mid = start + (end - start) / 2;
            // 要点3：=, <, > 分开讨论，mid 不+1也不-1
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }

        // 要点4: 循环结束后，单独处理start和end
        if (nums[start] == target) {
            return start;
        }
        if (nums[end] == target) {
            return end;
        }
        return -1;
    }
}
```

### Python
```python
class Solution:
    # @param nums: The integer array
    # @param target: Target number to find
    # @return the first position of target in nums, position start from 0 
    def binarySearch(self, nums, target):
        if not nums:
            return -1

        start, end = 0, len(nums) - 1
        # 用 start + 1 < end 而不是 start < end 的目的是为了避免死循环
        # 在 first position of target 的情况下不会出现死循环
        # 但是在 last position of target 的情况下会出现死循环
        # 样例：nums=[1，1] target = 1
        # 为了统一模板，我们就都采用 start + 1 < end，就保证不会出现死循环
        while start + 1 < end:
            # python 没有 overflow 的问题，直接 // 2 就可以了
            # java和C++ 最好写成 mid = start + (end - start) / 2
            # 防止在 start = 2^31 - 1, end = 2^31 - 1 的情况下出现加法 overflow
            mid = (start + end) // 2

            # > , =, < 的逻辑先分开写，然后在看看 = 的情况是否能合并到其他分支里
            if nums[mid] < target:
                start = mid
            elif nums[mid] == target:
                end = mid
            else: 
                end = mid

        # 因为上面的循环退出条件是 start + 1 < end
        # 因此这里循环结束的时候，start 和 end 的关系是相邻关系（1和2，3和4这种）
        # 因此需要再单独判断 start 和 end 这两个数谁是我们要的答案
        # 如果是找 first position of target 就先看 start，否则就先看 end
        if nums[start] == target:
            return start
        if nums[end] == target:
            return end

        return -1
```

使用了start + 1 < end, 而不是start < end 或者 start <= end  
二分法的模板中，整个程序架构分为两个部分：
- 通过 while 循环，将区间范围从 n 缩小到 2 （只有 start 和 end 两个点）。
- 在 start 和 end 中判断是否有解。  
而普通的start < end 或者 start <= end 在寻找目标最后一次出现的位置的时候，可能出现死循环。

为什么明明可以 start = mid + 1 偏偏要写成 start = mid?
大部分时候，mid 是可以 +1 和 -1 的。在一些特殊情况下，比如寻找目标的最后一次出现的位置时，当 target 与 nums[mid] 相等的时候，是不能够使用 mid + 1 或者 mid - 1 的。因为会导致漏掉解。那么为了节省脑力，统一写成 start = mid / end = mid 并不会造成任何解的丢失，并且也不会损失效率——log(n) 和 log(n+1) 没有区别。


# 时间复杂度低于O(N)的算法
在上一章中，我们讲到了一个O(logn)时间复杂度的算法，二分算法。只需要O(logn)的时间就可以成功进行搜索。而我们在第四章的时候，就已经讲到了，我们可以通过时间复杂度来推测算法，当我们发现需要时间复杂度为<O(N)的算法时，我们可以考虑使用二分搜索来解决问题。但是如果题目不能用二分搜索来解决，我们该使用什么算法来解决呢？

今天我们就来看一下几种同为logn时间复杂度的算法——**快速幂算法**、**辗转相除法**以及另外两种小于O(N)时间复杂度的算法——**质因数分解**和**分块检索法**。

## 快速幂算法
[LintCode 140](https://github.com/VJWQ/LeetCode-note/blob/master/method/BinarySearch/Lint-140-Fast-Power.md)

## 辗转相除法
### 算法介绍
辗转相除法， 又名欧几里德算法， 是求最大公约数的一种方法。它的具体做法是：用较大的数除以较小的数，再用除数除以出现的余数（第一余数），再用第一余数除以出现的余数（第二余数），如此反复，直到最后余数是0为止。如果是求两个数的最大公约数，那么最后的除数就是这两个数的最大公约数。

### 代码

Java:
```java
public int gcd(int big, int small) {
    if (small != 0) {
        return gcd(small, big % small);
    } else {
        return big;
    }
}
```
Python:
```python
def gcd(big, small):
    if small != 0:
        return gcd(small, big % small)
    else:
        return big
```
C++:
```cpp
int gcd(int big, int small) {
    if (small != 0) {
        return gcd(small, big % small);
    } else {
        return big;
    }
}
```

## 分解质因数
以 sqrt{n} 为时间复杂度的算法并不多见，最具代表性的就是分解质因数了。

### 具体步骤
记up = sqrt{n}，作为质因数k的上界, 初始化k=2。
当k <= up 且 n不为1 时，执行步骤3，否则执行步骤4。
当n被k整除时，不断整除并覆盖n，同时结果中记录k，直到n不能整出k为止。之后k自增，执行步骤2。
当n不为1时，把n也加入结果当中，算法结束。
几点解释
不需要判定k是否为质数，如果k不为质数，且能整出n时，n早被k的因数所除。故能整除n的k必是质数。
为何引入up？为了优化性能。当k大于up时，k已不可能整除n，除非k是n自身。也即为何步骤4判断n是否为1，n不为1时必是比up大的质数。
步骤2中，也判定n是否为1，这也是为了性能，当n已为1时，可早停。
### 代码
Java:
```java
public List<Integer> primeFactorization(int n) {
    List<Integer> result = new ArrayList<>();
    int up = (int) Math.sqrt(n);
    
    for (int k = 2; k <= up && n > 1; ++k) {
        while (n % k == 0) {
            n /= k;
            result.add(k);
        }
    }
    
    if (n > 1) {
        result.add(n);
    }
    
    return result;
}
```
Python:
```python
def primeFactorization(n):
    result = []
    up = int(math.sqrt(n));
    
    k = 2
    while k <= up and n > 1: 
        while n % k == 0:
            n //= k
            result.append(k)
        k += 1
            
    if n > 1:
        result.append(n)
        
    return result
```
C++:
```cpp
vector<int> primeFactorization(int n) {
    vector<int> result;
    int up = (int)sqrt(n);
    
    for (int k = 2; k <= up && n > 1; ++k) {
        while (n % k == 0) {
            n /= k;
            result.push_back(k);
        }
    }
    
    if (n > 1) {
        result.push_back(n);
    }
    
    return result;
}
```
### 复杂度分析
最坏时间复杂度O(sqrt (n) )。当n为质数时，取到其最坏时间复杂度。
空间复杂度O(log(n)), 当n质因数很多时，需要空间大，但总不会多于O(log(n))个
