```java
class Solution {
    public int fib(int n) {
        if(n<=1) return n;
        int prePre = 0, pre = 1;
        int ans=1;
        for(int i=2; i<=n; i++){
            ans = prePre%1000000007 + pre%1000000007;
            prePre = pre;
            pre = ans;
        }
        return ans % 1000000007;
    }
}
```