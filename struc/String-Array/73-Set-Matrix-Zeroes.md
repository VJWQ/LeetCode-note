### Java

#### Additional Memory Approach
```Java
class Solution {
    public void setZeroes(int[][] matrix) {
        int row = matrix.length;
        int col = matrix[0].length;
        
        Set<Integer> R = new HashSet<Integer>();
        Set<Integer> C = new HashSet<Integer>();

        for(int i = 0; i < row; i++){
            for(int j = 0; j < col; j++){
                if(matrix[i][j] == 0){
                    R.add(i);
                    C.add(j);
                }
            }
        }
        for(int i = 0; i < row; i++){
            for(int j = 0; j < col; j++){
                if(R.contains(i) || C.contains(j)){
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```

### Python
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        row = len(matrix)
        column = len(matrix[0])
        
        # Using set() instead of list(): Automatic deduplication
        rec1 = set()
        rec2 = set()
        
        for i in range(row):
            for j in range(column):
                if matrix[i][j] == 0:
                    rec1.add(i)
                    rec2.add(j)
                    
        for i in range(row):
            for j in range(column):
                if i in rec1 or j in rec2:
                    matrix[i][j] = 0
```
