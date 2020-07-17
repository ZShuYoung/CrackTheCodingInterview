## 思路

1. 可以组成顺子的充分条件是
   一、除去大小王，不能有重复的牌
   二、除去大小王之外，最大的比最小的差值小于5

```java
class Solution {
    public boolean isStraight(int[] nums) {
        Arrays.sort(nums);
        int joker = 0;
        for(int i=0; i<nums.length; i++){
            if(nums[i]==0){
                joker++;
                continue;
            }
            if(i!=0 && nums[i]==nums[i-1]){
                return false;
            }
        }
        return nums[4] - nums[joker] < 5;
    }
}
```