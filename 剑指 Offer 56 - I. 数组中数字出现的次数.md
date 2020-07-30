## 思路

1. 利用`res=0` 对所有数字做`亦或`操作， 最后得到的数即为答案两数亦或之后的结果
2. 找到一个数`marker`，其标识最后结果中二进制某一位上值为1的数。记两个只出现一次的数分别为a和b，那么有 `a & marker ==0  b & marker !=0` 。即通过maker可以把a和b分割开

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int res = 0;
        for(int n : nums){
            res ^= n;
        }
        int marker = 1;
        while((res & marker)==0){
            marker <<= 1;
        }
        int a=0, b=0;
        for(int n : nums){
            if((n & marker)!=0){
                a ^= n;
            }else{
                b ^= n;
            }
        }
        return new int[]{a,b};

    }
}
```

