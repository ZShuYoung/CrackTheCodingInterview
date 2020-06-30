## 思路

1. 利用一个特性：数字n与n-1做&运算会把最右边一位1置0

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int ans = 0;
        while(n!=0){
            n &= n-1;
            ans++;
        }
        return ans;
    }
}
```