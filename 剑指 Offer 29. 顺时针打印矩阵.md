## 思路

```java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0){
            return new int[0];
        }
        int n = matrix.length, m = matrix[0].length;
        int[] ans = new int[n*m];
        int top = 0, buttom = n-1, left = 0, right = m-1;
        int index = 0;
        while( top <= buttom && left <= right){
            for(int j=left; j<=right; j++){
                ans[index++] = matrix[top][j];
            }
            top++;

            for(int i=top; i<=buttom; i++){
                ans[index++] = matrix[i][right];
            }
            right--;

            // 因为上面top和right的值变化了所以下面还要判断一次
            if(top <= buttom){
                for(int j=right; j>=left; j--){
                    ans[index++] = matrix[buttom][j];
                }
                buttom--;
            }

            if(left <= right){
                for(int i=buttom; i>=top; i--){
                    ans[index++] = matrix[i][left];
                }
                left++;
            }
        }
        return ans;
    }
}
```