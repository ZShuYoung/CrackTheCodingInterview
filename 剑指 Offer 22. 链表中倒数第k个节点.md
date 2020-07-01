## 思路

1. 快慢指针
2. 准备一个preHead，快慢指针都指向preHead
3. 快指针先跑k步，之后快慢指针一起移动，当快指针指向null的时候慢指针指向倒数第k个结点

```java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ListNode fast = preHead, slow = preHead;
        while(k!=0 && fast!=null){
            fast = fast.next;
            k--;
        }
        while(fast.next!=null){
            slow=slow.next;
            fast=fast.next;
        }
        return slow.next;
    }
}
```