## 思路

1. 滑动窗口
2. 由于最少要有2个数，所以滑动窗口最开始的左右边界分别为1和2
3. 循环的结束条件为 `while(l<r && r<=(target+1)/2)` ， 考虑9=4+5这种场景，其实r是能取到(target+1)/2的
4. 根据窗口的值和target做比较判断窗口的滑动方式

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        List<int[]> list = new LinkedList<>();
        int l=1, r=2;
        while(l<r && r<=(target+1)/2){
            int sum = (l+r)*(r-l+1)/2;
            if(sum==target){
                int[] one = new int[r-l+1];
                for(int i=0; i<one.length; i++){
                    one[i] = l+i;
                }
                list.add(one);
                l++;
            }else if(sum<target){
                r++;
            }else{
                l++;
            }
        }
        return list.toArray(new int[0][]);
    }
}
```