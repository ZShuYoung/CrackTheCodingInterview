## 思路

1. 基于这样的一个结论 `a+b = (a^b) + (a&b)<<1 `

```
举个例子  5 + 7 = 12

1. 先求5 ^ 7    实际上得到的是不包含进位的结果
  101
^ 111
-----
  010

2. 再求5 & 7    发现左移一位就得到了应该进位的数
  101
& 111
-----
  101   左移一位得到1010

3. 再相加      正好是12
  0010
+ 1010
------
  1100   
```


```java
class Solution {
    // 递归的思路
    public int add(int a, int b) {
        if(b==0) return a;
        int part1 = a ^ b;
        int part2 = (a & b) << 1;
        return add(part1, part2);
    }
}
```