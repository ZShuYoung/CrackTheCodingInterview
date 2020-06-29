## 思路
1. 考虑二维数组的特性，从上到下 从左到右递增，所以从左下角开始查询。偏大就往右，偏小就往上
2. 直到到达边界如果还找不到，那就直接返回false

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0){
            return false;
        }
        int n = matrix.length;
        int m = matrix[0].length;
        // i>=0 && j<m 这里是边界判断
        for(int i=n-1, j=0; i>=0 && j<m; ){
            if(matrix[i][j] == target){
                return true;
            }else if(matrix[i][j] < target){
                j++;
            }else{
                i--;
            }
        }
        return false;
    }
}
```