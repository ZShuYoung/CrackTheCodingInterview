## 思路
1. 因为题干说明了所有数字都在0~n-1之间，所以使用一个int数组来标记每个数字出现的次数。下标为数字，对应值为数字出现的次数。
2. 遍历一波，只要出现值不为0就说明出现过，那就直接返回

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int[] hash = new int[nums.length];
        for(int n : nums){
            if(hash[n] == 0){
                hash[n] = 1;
            }else{
                return n;
            }
        }
        return 0;
    }
}
```