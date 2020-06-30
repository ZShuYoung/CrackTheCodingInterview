## 思路

1. 动态规划
2. `dp[i][j]` 表示点`[i][j]`机器人是否可以达到。那么就有状态转移方程 `dp[i][j] =  {数位之和大于k} &&(dp[i-1][j] || dp[i][j-1])`
3. 前一个位置状态会影响后面位置状态的往往考虑 `动态规划`

```java
class Solution {
    public int movingCount(int m, int n, int k) {
        // 定义一个横竖大一号的二维数组
        boolean[][] dp = new boolean[m+1][n+1];
        // dp[1][1]实际代表原始数组的[0][0]，因为必然可以达到，所以将dp[0][1]置为true作为初始化
        dp[0][1] = true;
        int ans = 0;
        for(int i=1; i<=m; i++){
            for(int j=1; j<=n; j++){
                // 因为二维数组大了一号，所以这里取真是数字的坐标计算数位之和
                int realI = i-1, realJ = j-1;
                if(!check(realI, realJ, k)){
                    continue;
                }
                if(dp[i-1][j] || dp[i][j-1]){
                    dp[i][j] = true;
                    ans++;
                }
            }
        }
        return ans;
    }

    private boolean check(int realI, int realJ, int k){
        int total = 0;
        while(realI!=0){
            total += realI % 10;
            realI /= 10;
        }
        while(realJ!=0){
            total += realJ % 10;
            realJ /= 10;
        }
        return total <= k;
    }
}
```