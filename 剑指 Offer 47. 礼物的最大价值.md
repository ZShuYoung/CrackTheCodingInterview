## 思路

1. 动态规划
2. 用一个二维数组dp[i][j]表示每个点所能掠夺的最大价值，于是有了状态转移方程 `dp[i][j] = max(dp[i-1][j], dp[i][j-1]) + grid[i][j]` 

```java
class Solution {
    public int maxValue(int[][] grid) {
        // 这里最外面套了一层0值就不需要对第一行第一列做初始化了
        int[][] dp = new int[grid.length+1][grid[0].length+1];
        for(int i=1; i<dp.length; i++){
            for(int j=1; j<dp[0].length; j++){
                dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]) + grid[i-1][j-1];
            }
        }
        return dp[dp.length-1][dp[0].length-1];
    }
}
```