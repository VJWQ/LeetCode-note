- Traversal
- DC
- DC with Memory: DP


### Python

```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        '''Traversal'''
    #     self.minimum = sys.maxsize
    #     self.traverse(triangle, 0, 0, 0)
    #     return self.minimum
    
    # def traverse(self, triangle, x, y, path_sum):
    #     if x == len(triangle):
    #         self.minimum = min(path_sum, self.minimum)
    #         return

    #     self.traverse(triangle, x + 1, y, path_sum + triangle[x][y])
    #     self.traverse(triangle, x + 1, y + 1, path_sum + triangle[x][y])

        '''DC'''
    #     return self.divide_conquer(triangle, 0, 0)

    # def divide_conquer(self, triangle, x, y):
    #     if x == len(triangle):
    #         return 0
        
    #     left = self.divide_conquer(triangle, x + 1, y)
    #     right = self.divide_conquer(triangle, x + 1, y + 1)
    #     return min(left, right) + triangle[x][y]

        '''DC with Memory: DP'''
        return self.divide_conquer(triangle, 0, 0, {})

    def divide_conquer(self, triangle, x, y, memo):
        # print(x, y)

        if x == len(triangle):
            # print('hi')
            return 0
        if (x, y) in memo:
            return memo[(x, y)]

        # print('left start')
        left = self.divide_conquer(triangle, x + 1, y, memo)
        # print('left end')

        # print('right start')
        right = self.divide_conquer(triangle, x + 1, y + 1, memo)
        # print('right end')

        # print(left, right, x, y, triangle[x][y])
        memo[(x, y)] = min(left, right) + triangle[x][y]
        # print(memo)
        return memo[(x, y)]
```

![](120-recursion.png)
#### Output with prints: 
```
0 0
left start
1 0
left start
2 0
left start
3 0
left start
4 0
left end
right start
4 1
right end
0 0 3 0 4
{(3, 0): 4}
left end
right start
3 1
left start
4 1
left end
right start
4 2
right end
0 0 3 1 1
{(3, 0): 4, (3, 1): 1}
right end
4 1 2 0 6
{(3, 0): 4, (3, 1): 1, (2, 0): 7}
left end
right start
2 1
left start
3 1
left end
right start
3 2
left start
4 2
left end
right start
4 3
right end
0 0 3 2 8
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8}
right end
1 8 2 1 5
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6}
right end
7 6 1 0 3
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6, (1, 0): 9}
left end
right start
1 1
left start
2 1
left end
right start
2 2
left start
3 2
left end
right start
3 3
left start
4 3
left end
right start
4 4
right end
0 0 3 3 3
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6, (1, 0): 9, (3, 3): 3}
right end
8 3 2 2 7
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6, (1, 0): 9, (3, 3): 3, (2, 2): 10}
right end
6 10 1 1 4
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6, (1, 0): 9, (3, 3): 3, (2, 2): 10, (1, 1): 10}
right end
9 10 0 0 2
{(3, 0): 4, (3, 1): 1, (2, 0): 7, (3, 2): 8, (2, 1): 6, (1, 0): 9, (3, 3): 3, (2, 2): 10, (1, 1): 10, (0, 0): 11}
```
