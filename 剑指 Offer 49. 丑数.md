## 思路

1. 动态规划
2. 我们都知道dp[i]依赖于dp[i]之前的数值，但是我们并不知道哪一个位置j上的数字再乘以2或3或5可以做到最小。
3. 我们用三个指针p2 p3 p5分别指向只有2 3 5相乘形成的丑数的下标，每一次比较的时候拿p2指向丑数的值\*2  p3指向丑数的值\*3  p5指向丑数的值\*5来比较取最小的值

```java
class Solution {
    public int nthUglyNumber(int n) {
        int p2=0, p3=0, p5=0;
        int[] dp = new int[n];
        dp[0] = 1;
        for(int i=1; i<n; i++){
            dp[i] = Math.min(2*dp[p2], Math.min(3*dp[p3], 5*dp[p5]));
            if(dp[i]==2*dp[p2]) p2++;
            if(dp[i]==3*dp[p3]) p3++;
            if(dp[i]==5*dp[p5]) p5++;
        }
        return dp[n-1];
    }
}
```