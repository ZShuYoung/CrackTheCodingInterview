```java
class Solution {
    public int numWays(int n) {
        if(n==0) return 1;
        if(n<=2) return n;
        int prePre = 1, pre = 2;
        int ans=1;
        for(int i=3; i<=n; i++){
            ans = prePre%1000000007 + pre%1000000007;
            prePre = pre;
            pre = ans;
        }
        return ans % 1000000007;
    }
}
```