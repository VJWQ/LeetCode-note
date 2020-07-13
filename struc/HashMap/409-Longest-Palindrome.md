- Greedy
- HashSet/HashMap

### Python
```python
class Solution:
    def longestPalindrome(self, s: str) -> int:
        '''Greedy'''
        # ans = 0
        # for v in collections.Counter(s).values():
        #     ans += v // 2 * 2   # 1 + 4 / 4 = 5
        #     if ans % 2 == 0 and v % 2 == 1:
        #         ans += 1
        # return ans
        
        '''HashSet'''
        hash = set()
        for c in s:
            if c not in hash:
                hash.add(c)
            else:
                hash.remove(c)
        # len(hash) is the number of the odd letters
        return len(s) - len(hash) + 1 if len(hash) > 0 else len(s)
```

### Java 

```java
public int longestPalindrome(String s) {
        Set<Character> set = new HashSet<>();
        for (char c : s.toCharArray()) {
            if (set.contains(c)) set.remove(c);
            else set.add(c);
        }

        int odd = set.size();
        return s.length() - (odd == 0 ? 0 : odd - 1);
    }
```
