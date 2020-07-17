## 思路

```
从n=1开始考虑如下：
1. 当n=1只剩一个人的时候，结果必然结果为0
2. 当n=2的时候，剩下人的值是 (0+m)%2
3. 当n=2的时候，剩下人的值是 ((0+m)%2+m)%3
```

```java
class Solution {
    public int lastRemaining(int n, int m) {
        int ans = 0;
        for(int i=2; i<=n; i++){
            ans = (ans + m) % i;
        }
        return ans;
    }
}
```