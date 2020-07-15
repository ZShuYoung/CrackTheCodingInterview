## 思路

1. 不能用加减乘除，条件判断那就考虑递归
2. 递归要用的话就要有条件判断，但是又不允许条件判断，这里就利用了 &&符号，当前面一段成立才会执行后面一段的逻辑

```java
class Solution {
    public int sumNums(int n) {
        int sum = n;
        // 这里的<0是为了凑条件表达式，换大于0也行
        boolean flag = (n>0) && ((sum += sumNums(n-1))<0);
        return sum;
    }
}
```