```java
class Solution {
    public int[] printNumbers(int n) {
        // 注意这里Math.pow()函数的返回是double类型
        int target = (int)Math.pow(10, n) - 1;
        int[] ans = new int[target];
        for(int i=1; i<=target; i++){
            ans[i-1] = i;
        }
        return ans;
    }
}
```