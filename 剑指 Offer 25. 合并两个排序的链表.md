```java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1==null) return l2;
        if(l2==null) return l1;
        ListNode p1 = l1, p2 = l2;
        ListNode preHead = new ListNode(0);
        ListNode ptr = preHead;
        while(p1!=null && p2!=null){
            if(p1.val <= p2.val){
                ptr.next = p1;
                ptr = p1;
                p1 = p1.next;
            }else{
                ptr.next = p2;
                ptr = p2;
                p2 = p2.next;
            }
        }
        if(p1==null){
            ptr.next=p2;
        }else{
            ptr.next=p1;
        }
        return preHead.next;
    }
}
```