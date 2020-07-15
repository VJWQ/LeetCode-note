### Python

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if not target:
            return 0

        '''1'''
        # for i in range(len(haystack) - len(needle) + 1):
        #     for j in range(len(needle)):
        #         if haystack[i + j] != needle[j]:
        #             break
        #     else:
        #         return i
        
        # return -1

        '''2'''
        for start in range(len(haystack)):
            if haystack[start: start + len(needle)] == needle:
                return start

        return -1
```

    
