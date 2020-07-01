```java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        if(head == null){
            return null;
        }
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ListNode ptr = preHead;
        while(ptr.next != null){
            if(ptr.next.val == val){
                ptr.next = ptr.next.next;
                break;
            }
            ptr = ptr.next;
        }
        return preHead.next;
    }
}
```