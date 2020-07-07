## 思路

1. 动态规划
2. dp[i]表示以i为结尾的连续子数组的最大和，那么就有递归方程 `dp[i] = max(dp[i-1]+nums[i], nums[i])` 
3. 遍历每个位置i，不断刷新最大值ans

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        int ans = dp[0];
        for(int i=1; i<nums.length; i++){
            dp[i] = Math.max(dp[i-1]+nums[i], nums[i]);
            ans = Math.max(dp[i], ans);
        }
        return ans;
    }
}
```