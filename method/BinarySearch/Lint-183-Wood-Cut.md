### Python
```python
class Solution:
    """
    @param L: Given n pieces of wood with length L[i]
    @param k: An integer
    @return: The maximum length of the small pieces
    """
    def woodCut(self, L, k):
        # write your code here
        if not L:
            return 0

        start, end = 1, max(L)
        while start + 1 < end:
            mid = (start + end) // 2
            if self.get_pieces(L, mid) >= k:
                start = mid
            else:
                end = mid
                
        if self.get_pieces(L, end) >= k:
            return end
        if self.get_pieces(L, start) >= k:
            return start
            
        return 0
        
    def get_pieces(self, L, length):
        pieces = 0
        for l in L:
            pieces += l // length
        return pieces
```

### Java
```java
// 对长度进行二分
public class Solution {
     /**
     *@param L: Given n pieces of wood with length L[i]
     *@param k: An integer
     *return: The maximum length of the small pieces.
     */
    public int woodCut(int[] L, int k) {
        int max = 0;
        // 切割最大长度，即所给数组中最大值
        for (int i = 0; i < L.length; i++) {
            max = Math.max(max, L[i]);
        }

        // 题目要求长度为正整数，最小切割长度为1
        int start = 1;
        int end = max;
        // 对长度进行二分，判断是否满足k，找出满足k的最大长度
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (count(L, mid) == k) {
                start = mid;
            }
            if (count(L, mid) < k) {
                end = mid;
            }
            if (count(L, mid) > k) {
                start = mid;
            }
        }

        // 求最大长度所以先检查end
        if (count(L, end) >= k) {
            return end;
        }

        if (count(L, start) >= k) {
            return start;
        }
        return 0;
    }
    
    // 计算当前切割长度标准下，数组能切多少个
    private int count(int[] L, int length) {
        int sum = 0;
        for (int i = 0; i < L.length; i++) {
            sum += L[i] / length;
        }
        return sum;
    }
}
```

