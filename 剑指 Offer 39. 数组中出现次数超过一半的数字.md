## 思路

1. 用一个count记录当前个数大于0的数字，相同加1，相反减1，减到0用新的数字替代
2. 因为有个数字个数超过一半，所以必然其对应的count大于0

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count=1;
        int element=nums[0];
        for(int i=1; i<nums.length; i++){
            if(nums[i]==element){
                count++;
            }else{
                if(count>1){
                    count--;
                }else{
                    element = nums[i];
                    count=1;
                }
            }
        }
        return element;
    }
}
```