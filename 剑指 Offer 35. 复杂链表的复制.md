## 思路

1. 在每个Node后面插入前一个Node的复制，这里记为Nodey
2. 于是就有了 `Node.next.random = Node.random.next`
3. 最后再分割成两个链表

```java
class Solution {
    public Node copyRandomList(Node head) {
        if(head==null){
            return null;
        }
        Node ptr = head;
        while(ptr!=null){
            Node copy = new Node(ptr.val);
            copy.next = ptr.next;
            ptr.next = copy;
            ptr = copy.next;
        }

        ptr = head;
        while(ptr!=null){
            // 注意这里，因为random可能指向null 所以要加一次校验
            if(ptr.random!=null){
                ptr.next.random = ptr.random.next;
            }
            ptr = ptr.next.next;
        }

        ptr = head;
        Node ans = ptr.next;
        Node nexPtr = ans;
        while(nexPtr.next!=null){
            ptr.next = nexPtr.next;
            ptr = ptr.next;
            nexPtr.next = ptr.next;
            nexPtr = nexPtr.next;
        }
        ptr.next = null;
        return ans;
    }
}
```
