```java
class Solution {
    public int singleNumber(int[] nums) {
        int[] total = new int[32];
        for(int n : nums){
            for(int i=0; i<32; i++){
                int mask = 1 << i;
                if((mask & n) != 0){
                    total[i]++;
                }
            }
        }
        int ans = 0;
        for(int i=0; i<32; i++){
            if(total[i] % 3!=0){
                ans += 1 << i;
            }
        }
        return ans;

    }
}
```