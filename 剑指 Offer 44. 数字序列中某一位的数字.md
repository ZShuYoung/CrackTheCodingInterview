## 思路

1. 找规律，总结如下
```
          每位几个数字(digit)      数字个数
1~9           1                    9*1
10~99         2                    9*10*2
100~999       3                    9*100*3
```

所以就可以通过三步来找到某一位的数字：
> - 先找到这意味的数字位于哪一个整数上面
> - 找到对应的位置

举个例子：n=13，因为n>9所以处于双位数10~99之间，然后从10开始计算 (13-9-1)/2 + 10 位于整数11之中，然后在(13-9-1)%2取到11的第二位1

```java
class Solution {
    public int findNthDigit(int n) {
        long start=1;
        int digit=1;
        while(n > 9 * start * digit){
            n -= 9 * start * digit;
            digit++;
            start *= 10;
        }
        int number = (int)(start + (n-1)/digit);
        return String.valueOf(number).charAt((n-1)%digit) - '0';
    }
}
```