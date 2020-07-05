## 思路

```java
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
        if(popped == null || popped == null || pushed.length != popped.length){
            return false;
        }
        Stack<Integer> stk = new Stack<>();
        int i = 0;
        for(int num : pushed){
            stk.push(num);
            while(!stk.isEmpty() && stk.peek()==popped[i]){
                stk.pop();
                i++;
            }
        }
        return stk.isEmpty();
    }
}
```