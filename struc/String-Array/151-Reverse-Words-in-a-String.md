- Built-in Functions
- Deque of Words
### Python

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        '''Built-in Functions'''
        # return " ".join(reversed(s.split()))
        
        '''Deque of Words'''
        from collections import deque
        
        left, right = 0, len(s) - 1
        res = []
        
        while left <= right:
            if s[left] == ' ':
                left += 1
            elif s[right] == ' ':
                right -= 1
            else: break
        
#         while left <= right and s[left] == ' ':
#             left += 1
#         while left <= right and s[right] == ' ':
#             right -= 1
            
        d = deque()
        word = []
        for left in range(left, right+1):
        # while left <= right:
            if s[left] != ' ':
                word.append(s[left])
            elif s[left] == ' ' and word:
                d.appendleft(''.join(word))
                word = []
            left += 1

        d.appendleft(''.join(word))
        
        return ' '.join(d)
```

        
