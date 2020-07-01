## 

```java
class Solution {
    // 迭代
    public double myPow(double x, int n) {
        double ans = 1.0;
        double y = x;
        int temp = n;
        while(temp!=0){
            if(temp%2!=0){
                ans *= y;
            }
            y = y*y;
            temp /= 2;
        }
        return n<0 ? 1/ans : ans;
    }

    // 递归
    public double myPow2(double x, int n) {
        if(n==0) return 1.0;
        if(n==1) return x;
        if(n==-1) return 1/x;
        double half = myPow(x, n/2);
        double ans = half * half;
        if(n % 2 ==1){
            return ans*x;
        }
        if(n % 2 ==-1){
            return ans*1/x;
        }
        return ans;
    }
}
```