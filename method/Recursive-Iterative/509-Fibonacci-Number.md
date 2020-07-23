- Recursive
- Bottom-Up Approach using Memoization


### Python
```python
class Solution:
    def fib(self, N: int) -> int:
        # '''Recursive'''
        # if N <= 1:
        #     return N
        # return self.fib(N-1) + self.fib(N-2)
    
        '''Bottom-Up Approach using Memoization'''
        a, b = 0, 1
        for _ in range(N):
            a, b = b, a + b
            
        return a  
```
