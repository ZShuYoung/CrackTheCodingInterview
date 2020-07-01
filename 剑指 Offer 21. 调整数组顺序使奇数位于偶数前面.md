## 思路

1. 双指针
2. 初始left指向左侧，right指向右侧。left向右找到第一个偶数 right向左找到第一个奇数，交换数值
3. 继续2的动作，知道left<=right

```java
class Solution {
    public int[] exchange(int[] nums) {
        int[] ans = new int[nums.length];
        ans = nums.clone();
        int left = 0, right = ans.length - 1;
        while(left < right){
            // 找到第一个偶数
            while(left < right && ans[left] % 2 != 0){
                left++;
            }
            // 找到第一个奇数
            while(left < right && ans[right] % 2 == 0){
                right--;
            }
            if(left < right){
                int temp = ans[left];
                ans[left] = ans[right];
                ans[right] = temp;
            }
        }
        return ans;
    }
}
```