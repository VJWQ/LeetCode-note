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
