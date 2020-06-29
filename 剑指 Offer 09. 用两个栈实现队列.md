## 思路

1. 一主一备两个队列，每次添加的时候都往主里面添加
2. deleteHead的时候先把主内的pop出来放入备，然后删除备peek位置的之后再把所有的反倒回主

```java
class CQueue {
    private Stack<Integer> primary;
    private Stack<Integer> backup;

    public CQueue() {
        this.primary = new Stack<>();
        this.backup = new Stack<>();
    }
    
    public void appendTail(int value) {
        primary.push(value);
    }
    
    public int deleteHead() {
        if(primary.isEmpty()){
            return -1;
        }
        while(!primary.isEmpty()){
            int top = primary.pop();
            backup.push(top);
        }
        int ans = backup.pop();
        while(!backup.isEmpty()){
            int top = backup.pop();
            primary.push(top);
        }
        return ans;
    }
}
```