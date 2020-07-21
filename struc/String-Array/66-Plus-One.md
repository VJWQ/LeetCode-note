- list->str->int->str->list
  - **map** function  
- Find 9

### Python

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        '''list->str->int->str->list'''
        # res = int("".join(map(str, digits)))
        # res += 1

        # return list(map(int, list(str(res))))

        '''Find 9'''
        res = []

        while digits and digits[-1] == 9:
            digits.pop()
            res.append(0)
        if not digits:
            return [1] + res
        else:
            digits[-1] += 1
            
            return digits + res
```
