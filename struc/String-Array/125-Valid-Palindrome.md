- Build-in function in Python: **.isalnum()**, **.filter(function, sequence)**
  - checks whether all the characters in a given string is alphanumeric or not.
  - filters the given sequence with the help of a function that tests each element in the sequence to be true or not.
  - Similar functions: **.isdigit()**, **.isalpha()**
- **.lower()** and **.upper()**


- Compare with Reverse
- Two Pointers

### Python

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        '''Compare with Reverse'''
        # filtered_char = filter(lambda ch: ch.isalnum(), s)
        # lower_case = map(lambda ch: ch.lower(), filtered_char)
        # ls = list(lower_case)
        # # return ls == reversed(ls)
        # return ls == ls[::-1]
        
        '''Two Pointers-1'''
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


        '''Two Pointers-2'''
        left, right = 0, len(s) - 1
        while left < right:
            while left < right and not self.is_valid(s[left]):
                left += 1
            while left < right and not self.is_valid(s[right]):
                right -= 1
            if left < right and s[left].lower() != s[right].lower():
                return False
            left += 1
            right -= 1
        return True

    def is_valid(self, char):
        return char.isdigit() or char.isalpha()
```

