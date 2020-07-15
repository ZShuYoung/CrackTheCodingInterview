## 思路

1. 遍历每一个数，用一个minPrice记录当前的最低价格；用ans记录当前的最高利润

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length < 2){
            return 0;
        }
        int minPrice = prices[0];
        int ans = 0;
        for(int i=1; i<prices.length; i++){
            ans = Math.max(ans, prices[i]-minPrice);
            minPrice = Math.min(prices[i], minPrice);
        }
        return ans;
    }
}
```