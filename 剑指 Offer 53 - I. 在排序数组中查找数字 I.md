## 思路

1. 两次二分查找，分别找出左边界和右边界

```java
class Solution {
    public int search(int[] nums, int target) {
        int l = findLeft(nums, target);
        int r = findRight(nums, target);
        return l==-1 ? 0 : r-l+1;
    }

    private int findLeft(int[] nums, int target){
        int l=0, r=nums.length-1;
        int ans = -1;
        // 二分查找这里是 <=
        while(l <= r){
            int mid = l+(r-l)/2;
            if(nums[mid]<target){
                l=mid+1;
            }else if(nums[mid]>target){
                r=mid-1;
            }else{
                ans = mid;
                r=mid-1;
            }
        }
        return ans;
    }

    private int findRight(int[] nums, int target){
        int l=0, r=nums.length-1;
        int ans = -1;
        while(l <= r){
            int mid = l+(r-l)/2;
            if(nums[mid]<target){
                l=mid+1;
            }else if(nums[mid]>target){
                r=mid-1;
            }else{
                ans = mid;
                l=mid+1;
            }
        }
        return ans;
    }
}
```