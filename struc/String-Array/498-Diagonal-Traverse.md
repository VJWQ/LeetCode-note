### Java

```java
class Solution {
    public int[] findDiagonalOrder(int[][] matrix) {
        if (matrix == null || matrix.length == 0) return new int[0];
        int row = 0, col = 0, m = matrix.length, n = matrix[0].length, output [] = new int[m * n];
        for (pos = 0; pos < m * n; pos++) {
            output[pos] = matrix[row][col];
            if ((row + col) % 2 == 0) {
                // The direction is always up when the sum of row & col is even
                // For last column, go down
                if (col == n-1) { row++; }                
                // For first row & non-last columns, go right
                else if (row == 0) { col++; }
                // For not first row & non-last columns, go up and to the right
                else { row--; col++; }
            } else {
                // The direction is always down when the sum of row & col is odd
                // For last row, go right
                if (row == m-1) { col++; } 
        
                //  For non-last row & first column, go down
                else if (col == 0) { row++; }
        
                // For non-last row & non-first column, go down and to the left
                else { row++; col--; }
            }
        }
        return output;
    }
}
```

### Python

```python
class Solution:
    def findDiagonalOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix or not matrix[0]:
            return []
        M, N = len(matrix), len(matrix[0])
        # matrix_num = M * N
        res = [0]*(M*N)
        r, c = 0, 0
        for i in range(M*N):
            res[i] = matrix[r][c]
            if(r+c)%2 == 0:
                if c == N - 1:
                    r += 1      # Move down
                elif r == 0:
                    c += 1      # Move right 
                else:
                    r -= 1      # Move up-right
                    c += 1
            else:
                if r == M - 1:
                    c += 1      # Move right
                elif c == 0:
                    r += 1      # Move down
                else:
                    r += 1      # Move down-left
                    c -= 1
        return res
```

### C++: DFS

```cpp
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& matrix) {
        vector<int> res;
        if(matrix.empty()) return res;
        int m = matrix.size(), n = matrix[0].size();
        vector<pair<int, int>> dir({{-1, 1}, {1, -1}}); // 事先规定两个方向的移动参数
        DFS(matrix, res, 0, 0, m, n, dir, 0);
        return res;
    }
private:
    void DFS(vector<vector<int>>& matrix, vector<int>& res, int r, int c, int m, int n, vector<pair<int, int>>& dir, int d){
        if(res.size() == m * n) return;
        res.push_back(matrix[r][c]);
        int R = r + dir[d].first;
        int C = c + dir[d].second;
        if(R < 0 || C < 0 || R >= m || C >= n){ // 如果超出边界
            d = (d + 1) % 2; // 改变方向
            if(R < 0 || R >= m) R = r, C = c + 1; // 对应右上方方向超出
            if(C < 0 || C >= n) R = r + 1, C = c; // 对应左下方方向超出
        }
        DFS(matrix, res, R, C, m, n, dir, d);
    }
};
```
