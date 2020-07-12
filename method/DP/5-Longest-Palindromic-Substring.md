https://leetcode.com/problems/longest-palindromic-substring

- Brute Force
- Dynamic Programming
- Expand Around Center
- Manacher's Algorithm

### Python
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        '''Brute Force'''
        if len(s) < 2: return s
                
        for length in range(len(s), 0, -1):
            for begin in range(len(s) - length + 1):
                if self.is_palindrome(s, begin, begin + length - 1):
                    return s[begin:begin + length]
        
        return ""
        
        # max_len = 1
        # size = len(s)
        # res = 0
        # for begin in range(size - 1):
        #     for end in range(begin + 1, size):
        #         if end - begin + 1 > max_len and self.is_palindrome(s, begin, end):
        #             max_len = end - begin + 1
        #             res = begin
        # return s[res:res + max_len]
    
    
    def is_palindrome(self, s, left, right):
        while left <= right and s[left] == s[right]:
            left += 1 
            right -= 1 
        return left >= right


        '''Expand Around Center'''
    #     size = len(s)
    #     if size < 2: return s
    #     max_len = 1
    #     begin = 0

    #     for i in range(size):       # left == right: odd; left + 1 == right: even
    #         odd_len = self.center_spread(s, size, i, i)     
    #         even_len = self.center_spread(s, size, i, i + 1)

    #         cur_max_sub = max(odd_len, even_len)
    #         if cur_max_sub > max_len:
    #             max_len = cur_max_sub
    #             begin = i - (max_len - 1) // 2
        
    #     return s[begin:begin+max_len]

    
    # def center_spread(self, s, size, left, right):
    #     i, j = left, right

    #     while i >= 0 and j < size and s[i] == s[j]:
    #         i -= 1
    #         j += 1
    #     return j - i - 1

        
        '''Dynamic Programming'''
        size = len(s)
        if size < 2: return s

        dp = [[False for _ in range(size)] for _ in range(size)]

        max_len = 1
        start = 0

        for i in range(size):
            dp[i][i] = True

        for j in range(1, size):
            for i in range(0, j):
                if s[i] != s[j]:
                    dp[i][j] = False
                else:
                    if j - i < 3:
                        dp[i][j] = True
                    else:
                        dp[i][j] = dp[i + 1][j - 1]
                        
                cur_len = j - i + 1

                if dp[i][j] and cur_len > max_len:
                    max_len = cur_len
                    start = i
        return s[start:start + max_len]


        '''Manacher's Algorithm'''
    #     # 特判
    #     size = len(s)
    #     if size < 2:
    #         return s

    #     # 得到预处理字符串
    #     t = "#"
    #     for i in range(size):
    #         t += s[i]
    #         t += "#"
    #     # 新字符串的长度
    #     t_len = 2 * size + 1
    #     # 当前遍历的中心最大扩散步数，其值等于原始字符串的最长回文子串的长度
    #     max_len = 1
    #     # 原始字符串的最长回文子串的起始位置，与 max_len 必须同时更新
    #     start = 0

    #     for i in range(t_len):
    #         cur_len = self.center_spread(t, i)
    #         if cur_len > max_len:
    #             max_len = cur_len
    #             start = (i - max_len) // 2
    #     return s[start: start + max_len]

    # def center_spread(self, s, center):
    #     size = len(s)
    #     i = center - 1
    #     j = center + 1
    #     step = 0
    #     while i >= 0 and j < size and s[i] == s[j]:
    #         i -= 1
    #         j += 1
    #         step += 1
    #     return step
```
