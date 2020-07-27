## 思路

```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode pa=headA, pb=headB;
        while(true){
            if(pa==pb) return pa;
            pa = pa==null ? headA : pa.next;
            pb = pb==null ? headB : pb.next;
        }
    }
}
```