## 思路

1. 动态规划
2. 对于一根长度n的绳子，记剪完之后的最大长度为f(n)，实际上f(n)可以转换为在[1,f(n-1)]  [2,f(n-2)]  [3,f(n-3)] ... 中取最大的值
3. 对于每一个2，3 或者f(n-2)又可以选择是不减还是剪，所以就有状态转移公式 `dp[n] = max(dp[n], max(i, dp[i]) * max(n-i, dp[n-i])`

```java
class Solution {
    public int cuttingRope(int n) {
        int[] dp = new int[n+1];
        dp[1] = 1;
        for(int i=2; i<=n; i++){
            for(int j=1; j<=i/2; j++){
                dp[i] = Math.max(dp[i], Math.max(j, dp[j]) * Math.max(i-j, dp[i-j]));
            }
        }
        return dp[n];
    }
}
```