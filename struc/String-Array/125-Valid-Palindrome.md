- Build-in function in Python: **isalnum()**, **filter(function, sequence)**
  - checks whether all the characters in a given string is alphanumeric or not.
  - filters the given sequence with the help of a function that tests each element in the sequence to be true or not.


- Compare with Reverse
- Two Pointers

### Python

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        '''Compare with Reverse'''
        filtered_char = filter(lambda ch: ch.isalnum(), s)
        lower_case = map(lambda ch: ch.lower(), filtered_char)
        ls = list(lower_case)
        rev_ls = ls[::-1]
        return ls == rev_ls
        
        '''Two Pointers'''
#         newline = []
#         for i in s.lower():
#             if i.isalnum():
#             # if (i >= 'a' and i <= 'z') or (i >= str(0) and i <= str(9)):
#                 newline.append(i)
        
#         return self.validation("".join(newline))

#     def validation(self, s):
#         left, right = 0, len(s) - 1
#         while left < right and s[left] == s[right]:
#             left += 1
#             right -= 1
#         return left >= right
```

