## 思路

1. 动态规划
2. dp[i]表示num前i位可以组成的翻译方法的种数
3. 状态转移方程dp[i+1] = dp[i-1] + dp[i-2] (i-1和i组成的数字位于10到25之间) 

```java
class Solution {
    public int translateNum(int num) {
        // dp[i]表示num前i位可以组成的翻译方法的钟数
        // dp[i+1] = dp[i-1] + dp[i-2](i-1和i组成的数字位于10到25之间)
        char[] chars = String.valueOf(num).toCharArray();
        int[] dp = new int[chars.length + 1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i < dp.length; i++) {
            dp[i] = dp[i - 1];
            int idx = i - 1;
            int pre = idx - 1;
            int t = (chars[pre] - '0') * 10 + (chars[idx] - '0');
            if (t >= 10 && t <= 25) {
                dp[i] += dp[i - 2];
            }
        }
        return dp[dp.length - 1];
    }
}
```