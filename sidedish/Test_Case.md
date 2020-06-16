# Input functions in Python
- `raw_input()` : returning a string without '\n' at the end. Deleted in Python 3 and replaced with `input()`.  

- `input()`: similar to `raw_input()`. **deal with one line data separated by spaces**  

- `sys.stdin()`: read in all input lines. Including '\n' at the end. **deal with multiple lines data**  

    - `sys.stdin.readline()`: read in one line

    - `sys.stdin.readlines()`: read in multiple lines until ctrl+D+enter.

## Process and formation
- `map(func, iter)`: returns a map object(iterator) of the results after applying the given function to each item of a given iterable (list, tuple etc.)  
- `list()`: takes sequence types and converts them to lists  
- `.split()`: splits a string into a list. **deal with targes in the string**  
- `.strip()/.strip("characters")`: remove spaces/characters at the beginning and at the end of the string.  **deal with targes at the beginning/end**  
    - `data=list(map(int,input().split()))`  


# Porcess input data: templates and examples

```python
def main():
    import sys
    import io
    def readlines():
        for line in io.TextIOWrapper(sys.stdin.buffer, encoding='utf-8'):
            yield line.strip('\n')

    lines = readlines()
    while True:
        try:
            # Deal with input details: convert to desired form
            line = next(lines)
            nums = stringToIntegerList(line);
            line = next(lines)
            target = int(line);
            
            # Call the function
            ret = Solution().twoSum(nums, target)
            
            # Return the output
            out = integerListToString(ret);
            print(out)
        except StopIteration:
            break

if __name__ == '__main__':
    main()
```

```python
def main():
    import sys
    import io
    def readlines():
        for line in io.TextIOWrapper(sys.stdin.buffer, encoding='utf-8'):
            yield line.strip('\n')

    lines = readlines()
    while True:
        try:
            # Deal with input details: convert if needed
            line = next(lines)
            l1 = stringToListNode(line);
            line = next(lines)
            l2 = stringToListNode(line);
            
            # Call the function
            ret = Solution().addTwoNumbers(l1, l2)
            
            # Return the output: convert if needed
            out = listNodeToString(ret);
            print(out)
        except StopIteration:
            break

if __name__ == '__main__':
    main()
```

```python
def main():
    import sys
    import io
    def readlines():
        for line in io.TextIOWrapper(sys.stdin.buffer, encoding='utf-8'):
            yield line.strip('\n')

    lines = readlines()
    while True:
        try:
            line = next(lines)
            s = stringToString(line);
            
            ret = Solution().longestPalindrome(s)

            out = (ret);
            print(out)
        except StopIteration:
            break

if __name__ == '__main__':
    main()
```
