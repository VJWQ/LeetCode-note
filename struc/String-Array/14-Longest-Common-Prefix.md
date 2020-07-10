### Python
https://leetcode-cn.com/problems/longest-common-prefix/

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs: return ""
        
        '''horizontal scan'''
        # res = strs[0]
        # i = 1
        # while i < len(strs):
        #     while strs[i].find(res) != 0:
        #         res = res[0:len(res)-1]
        #     i += 1
        # return res
        
        '''vertical scan'''
        # length, count = len(strs[0]), len(strs)
        # for i in range(length):
        #     c = strs[0][i]
        #     for j in range(count):
        #         if i == len(strs[j]) or strs[j][i] != c:
        #             return strs[0][:i]        
        # return strs[0]
    
        '''dictionary'''
        # res = []
        # strs.sort()
        # n = len(strs)
        # a = strs[0]
        # b = strs[n-1]
        # for i in range(min(len(a), len(b))):
        #     if a[i] == b[i]:
        #         res.append(a[i])
        #     else:
        #         break
        # return "".join(res)
        
        '''divide and conquer'''
        def lcp(start, end):
            if start == end:
                return strs[start]

            mid = (start + end) // 2
            lcpLeft, lcpRight = lcp(start, mid), lcp(mid + 1, end)
            minLength = min(len(lcpLeft), len(lcpRight))
            for i in range(minLength):
                if lcpLeft[i] != lcpRight[i]:
                    return lcpLeft[:i]

            return lcpLeft[:minLength]

        return "" if not strs else lcp(0, len(strs) - 1)
```
