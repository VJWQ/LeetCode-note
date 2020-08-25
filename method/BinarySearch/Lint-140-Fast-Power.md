- Recursive
- Binary

### Python
```python
class Solution:
    """
    @param a: A 32bit integer
    @param b: A 32bit integer
    @param n: A 32bit integer
    @return: An integer
    """
    def fastPower(self, a, b, n):
        '''
        (a + b) % c == (a % c + b % c) % c
        (a * b) % c == (a % c * b % c) % c
        (a - b) % c == (a % c - b % c) % c
        (a / b) % c != (a % c / b % c + c) % c // +c: ensure a positive result
        a^n = (a^n//2)^2        n % 2 == 0
            = (a^n//2)^2*a      n % 2 == 1
        '''
        
        '''Recursive'''
        # if n == 0:
        #     return 1 % b
            
        # if n == 1:
        #     return a % b 
            
        # power = self.fastPower(a, b, n // 2)
        # power = (power * power) % b
        
        
        # if n % 2 == 1:
        #     power = (power * a) % b
        
        # return power
        
        
        '''Binary'''
        ans = 1 
        while n > 0:
            if n % 2 == 1: 
                ans = (ans * a) % b 
            a = a * a % b 
            n = n // 2 
        return ans % b
``
