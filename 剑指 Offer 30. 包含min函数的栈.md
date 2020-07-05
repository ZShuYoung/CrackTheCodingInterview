## 思路

1. 两个栈，一个用来存数据，一个用来保存最小值
2. 基于这样一个思想：`当有更小的值push进来的时候，同时也要推入min栈`。因为后面有大的值进来，也是先出去，不会影响min栈的内容

```java
class MinStack {
    private Stack<Integer> data;
    private Stack<Integer> min;

    /** initialize your data structure here. */
    public MinStack() {
        data = new Stack<>();
        min = new Stack<>();
    }
    
    public void push(int x) {
        data.push(x);
        if(min.isEmpty() || min.peek()>=x){
            min.push(x);
        }
    }
    
    public void pop() {
        // 注意这里用equals
        if(data.pop().equals(min.peek())){
            min.pop();
        }
    }
    
    public int top() {
        return data.peek();
    }
    
    public int min() {
        return min.peek();
    }
}
```