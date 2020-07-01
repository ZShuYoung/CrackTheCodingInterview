## 思路

### 迭代
1. 迭代终止条件为`head==null || head.next==null`
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        ListNode rever = reverseList(head.next);
        ListNode ptr = rever;
        // 找到尾部
        while(ptr.next!=null){
            ptr = ptr.next;
        }
        ptr.next = head;
        // 不能忘记这里head已经是尾了，所以next指向null
        head.next = null;
        return rever;
    }
}
```

### 递归
1. 准备三个指针cur nex nn  nn是用来保存下一个节点的，因为nex需要翻转
2. 循环结束条件为 `nex != null`

```java
class Solution {
    public ListNode reverseList2(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        ListNode rever = reverseList(head.next);
        ListNode ptr = rever;
        while(ptr.next!=null){
            ptr = ptr.next;
        }
        ptr.next = head;
        head.next = null;
        return rever;
    }
}
```