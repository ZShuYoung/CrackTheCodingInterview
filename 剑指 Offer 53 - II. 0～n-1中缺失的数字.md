## 思路

1. 二分查找

```java
class Solution {
    public int missingNumber(int[] nums) {
        int max = nums.length;
        int l=0, r=nums.length-1;
        if(nums[r]==r) return max;
        while(l<r){
            int mid = l+(r-l)/2;
            if(nums[mid]==mid){
                l = mid+1;
            }else {
                // 这里是r
                r = mid;
            }
        }
        return l;
    }
}
```