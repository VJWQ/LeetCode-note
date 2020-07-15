- Brute Force
- Rabin–Karp algorithm (hash)

### Python

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if not source or not target:
            return 0

        '''Brute Force-1'''
        # for i in range(len(haystack) - len(needle) + 1):
        #     for j in range(len(needle)):
        #         if haystack[i + j] != needle[j]:
        #             break
        #     else:
        #         return i
        
        # return -1

        '''Brute Force-2'''
        for start in range(len(haystack)):
            if haystack[start: start + len(needle)] == needle:
                return start

        return -1
```

```java
class Solution {
    // Rabin–Karp algorithm
    public int BASE = 1000000;
    public int strStr(String haystack, String needle) {
        if (haystack == null || needle == null) {
            return -1;
        }

        int m = needle.length();
        if (m == 0) {
            return 0;
        }

        int power = 1;
        for (int i = 0; i < m; i++) {
            power = (power * 31) % BASE;
        }

        int targetCode = 0;
        for (int i = 0; i < m; i++) {
            targetCode = (targetCode * 31 + needle.charAt(i)) % BASE;
        }

        int hashCode = 0;
        for (int i = 0; i < haystack.length(); i++) {
            // abc + d
            hashCode = (hashCode * 31 + haystack.charAt(i)) % BASE;
            if (i < m - 1) {
                continue;
            }

            // abcd- a
            if (i >= m) {
                hashCode = hashCode - (haystack.charAt(i - m) * power) % BASE;
                if (hashCode < 0) {
                    hashCode += BASE;
                }
            }
            // double check the string
            if (hashCode == targetCode) {
                if (haystack.substring(i - m + 1, i + 1).equals(needle)) {
                    return i - m + 1;
                }
            }
        }
    return -1;
    }
}
```

    
