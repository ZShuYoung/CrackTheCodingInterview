## 思路

1. 首先考虑数组中不存在相同的数字，那么对于左右边界l和r，如果有 `nums[l]<nums[r]` 则说明数组未旋转，那么最小数字必然是 `nums[l]`
2. 取中间数mid，如果有 `nums[l]<nums[mid]` ，那么说明左半边是升序的，最小数在右半边，令 `l=mid+1`
3. 如果如果有 `nums[l]>nums[mid]` ，那么说明转折点在左半边并且可能是mid，所以令 `r=mid`
4. 最终情况是l==r返回nums[l]
5. 如果存在相同的数，当 `nums[l]==nums[mid]` 的时候，使用l++,跳过相同的数继续循环

```java
class Solution {
    public int minArray(int[] numbers) {
        int l=0, r=numbers.length-1;
        while(l<r){
            if(numbers[l]<numbers[r]){
                return numbers[l];
            }
            int mid = l+(r-l)/2;
            // 这里l++很关键
            if(numbers[l]==numbers[mid]){
                l++;
                continue;
            }else if(numbers[l]<numbers[mid]){
                l=mid+1;
            }else{
                r=mid;
            }
        }
        return numbers[l];
    }
}
```