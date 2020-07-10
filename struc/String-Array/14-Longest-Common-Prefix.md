### Python
https://leetcode-cn.com/problems/longest-common-prefix/

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs: return ""
        
        '''Horizontal scanning'''
        # res = strs[0]
        # i = 1
        # while i < len(strs):
        #     while strs[i].find(res) != 0:
        #         res = res[0:len(res)-1]
        #     i += 1
        # return res
        
        '''Vertical scanning'''
        # length, count = len(strs[0]), len(strs)
        # for i in range(length):
        #     c = strs[0][i]
        #     for j in range(count):
        #         if i == len(strs[j]) or strs[j][i] != c:
        #             return strs[0][:i]        
        # return strs[0]
    
        '''Dictionary'''
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
### Java
- Horizontal scanning
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
       String prefix = strs[0];
        for (int i = 1; i < strs.length; i++)
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }        
        return prefix;
    }
}
```

- Vertical Scanning
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";
    for (int i = 0; i < strs[0].length() ; i++){
        char c = strs[0].charAt(i);
        for (int j = 1; j < strs.length; j ++) {
            if (i == strs[j].length() || strs[j].charAt(i) != c)
                return strs[0].substring(0, i);             
        }
    }
    return strs[0];
}
```

- Divide and Conquer
```java
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";    
        return longestCommonPrefix(strs, 0 , strs.length - 1);
}

private String longestCommonPrefix(String[] strs, int l, int r) {
    if (l == r) {
        return strs[l];
    }
    else {
        int mid = (l + r)/2;
        String lcpLeft =   longestCommonPrefix(strs, l , mid);
        String lcpRight =  longestCommonPrefix(strs, mid + 1,r);
        return commonPrefix(lcpLeft, lcpRight);
   }
}

String commonPrefix(String left,String right) {
    int min = Math.min(left.length(), right.length());       
    for (int i = 0; i < min; i++) {
        if ( left.charAt(i) != right.charAt(i) )
            return left.substring(0, i);
    }
    return left.substring(0, min);
}
```
