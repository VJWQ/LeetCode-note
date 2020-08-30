- Build-in Function
- Iteration: Cascading
- Recursion: Backtracking
- Binary Sorted

### Python

```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        '''Build-in Function'''
        # res = []
        # for i in range(len(nums)+1):
        #     for tmp in itertools.combinations(nums, i):
        #         res.append(tmp)
        # return res

        '''Iteration: Cascading'''
        # n = len(nums)
        # output = [[]]
        # for num in nums:
        #     output += [cur + [num] for cur in output]
        # return output
    
        '''Recursion: Backtracking-1'''
        # if not nums: return []
        # n = len(nums)
        # res =[]

        # def dfs(path, start):
        #     res.append(path[:])
        #     for i in range(start, n):
        #         path.append(nums[i])
        #         dfs(path, i + 1)
        #         path.pop()
                
        # dfs([], 0)
        # return res
    
        '''Recursion: Backtracking-2'''
        # if not nums: return []
        # n = len(nums)
        # res =[]
    
        # def dfs(i, tmp):
        #     res.append(tmp)
        #     for j in range(i, n):
        #         dfs(j + 1,tmp + [nums[j]] )
        # dfs(0, [])
        # return res  

        '''Binary Sorted'''
        n = len(nums)
        output = []
        
        for i in range(2**n, 2**(n + 1)):
            # generate bitmask, from 0..00 to 1..11
            bitmask = bin(i)[3:]
            
            # append subset corresponding to that bitmask
            output.append([nums[j] for j in range(n) if bitmask[j] == '1'])
        
        return output
```

> 用非递归（Non-recursion / Iteration）的方式实现全子集问题，有两种方式：
> - [进制转换 (binary)](#基于进制转换的方法)
> - [宽度优先搜索 (Breadth-first Search)](#基于BFS的方法)

## 基于进制转换的方法
思路就是使用一个 正整数的二进制表示 的第 i 位是 1 还是 0 来代表集合的第 i 个数取或者不取。因为从 0 到 2^n - 1 总共 2^n 个整数，正好对应集合的 2^n 个子集。
比如 {1，2，3} 的子集可以用 0 到 7 来表示。

> 0 -> 000 -> {}  
> 1 -> 001 -> {3}  
> 2 -> 010 -> {2}  
> 3 -> 011 -> {2,3}  
> 4 -> 100 -> {1}  
> 5 -> 101 -> {1,3}  
> 6 -> 110 -> {1,2}  
> 7 -> 111 -> {1,2,3}
  
### Java:
```java
class Solution {
    /**
     * @param S: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        int n = nums.length;
        Arrays.sort(nums);
        for (int i = 0; i < (1 << n); i++) {
            List<Integer> subset = new ArrayList<Integer>();
            for (int j = 0; j < n; j++) {
                if ((i & (1 << j)) != 0) {
                    subset.add(nums[j]);
                }
            }
            result.add(subset);
        }
        
        return result;
    }
}
```
### C++
```cpp
class Solution {
public:
    /**
     * @param nums: A set of numbers
     * @return: A list of lists
     */
    vector<vector<int>> subsets(vector<int> &nums) {
        vector<vector<int>> result;
        const int n = nums.size();
        sort(nums.begin(), nums.end());
        for (int i = 0; i < (1 << n); i++) {
            vector<int> subset;
            for (int j = 0; j < n; j++) {
                if ((i & (1 << j)) != 0) {
                    subset.push_back(nums[j]);
                }
            }
            result.push_back(std::move(subset));
        }
        
        return result;
    }
};
```
### Python
```python
class Solution:
    def subsets(self, nums):
        result = []
        n = len(nums)
        nums.sort()
        for i in range(1 << n):
            subset = []
            for j in range(n):
                if (i & (1 << j)) != 0:
                    subset.append(nums[j])
            result.append(subset)
        return result
```

## 基于BFS的方法
在 BFS 那节课的讲解中，我们很少提到用 BFS 来解决找所有的方案的问题。事实上 BFS 也是可以用来做这件事情的。
用 BFS 来解决该问题时，层级关系如下：

> 第一层: []  
> 第二层: [1] [2] [3]  
> 第三层: [1, 2] [1, 3], [2, 3]  
> 第四层: [1, 2, 3]  
> 每一层的节点都是上一层的节点拓展而来。

### Java
```java
public class Solution {
    
    /*
     * @param nums: A set of numbers
     * @return: A list of lists
     */
    public List<List<Integer>> subsets(int[] nums) {
        // List vs ArrayList （google）
        List<List<Integer>> results = new LinkedList<>();
        
        if (nums == null) {
            return results; // 空列表
        }
        
        Arrays.sort(nums);
        
        // BFS
        Queue<List<Integer>> queue = new LinkedList<>();
        queue.offer(new ArrayList<Integer>());
        
        while (!queue.isEmpty()) {
            List<Integer> subset = queue.poll();
            results.add(subset);
            
            for (int i = 0; i < nums.length; i++) {
                if (subset.size() == 0 || subset.get(subset.size() - 1) < nums[i]) {
                    List<Integer> nextSubset = new ArrayList<Integer>(subset);
                    nextSubset.add(nums[i]);
                    queue.offer(nextSubset);
                }
            }
        }
        
        return results;
    }
}
```
### C++
```cpp
class Solution {
public:
    /*
     * @param nums: A set of numbers
     * @return: A list of lists
     */
    vector<vector<int>> subsets(vector<int> &nums) {
        vector<vector<int>> results;
        sort(nums.begin(), nums.end());
        
        // BFS
        queue<vector<int>> que;
        que.push({});
        
        while (!que.empty()) {
            vector<int> subset = que.front();
            que.pop();
            results.push_back(subset);
            
            for (int i = 0; i < nums.size(); i++) {
                if (subset.size() == 0 || subset.back() < nums[i]) {
                    vector<int> nextSubset = subset;
                    nextSubset.push_back(nums[i]);
                    que.push(nextSubset);
                }
            }
        }
        
        return results;
    }
};
```
### Python
```python
class Solution:
    def subsets(self, nums):
        results = []

        if not nums:
            return results

        nums.sort()

        # BFS
        queue = deque()
        queue.append([])

        while queue:
            subset = queue.popleft()
            results.append(subset)

            for i in range(len(nums)):
                if not subset or subset[-1] < nums[i]:
                    nextSubset = list(subset)
                    nextSubset.append(nums[i])
                    queue.append(nextSubset)

        return results
```


