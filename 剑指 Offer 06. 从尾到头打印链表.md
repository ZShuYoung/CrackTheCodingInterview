## 思路
1. 两次遍历，第一次计算出链表长度，从而定义数组长度
2. 第二次遍历，倒序记录到数组中

```java
class Solution {
    public int[] reversePrint(ListNode head) {
        if(head == null){
            return new int[0];
        }
        // 第一次遍历，主要是记录length
        ListNode ptr = head;
        int length = 0;
        while(ptr != null){
            length++;
            ptr = ptr.next;
        }

        // 第二次遍历，倒序记录链表值到数组
        int[] ans = new int[length];
        ptr = head;
        length--;
        while( ptr != null){
            ans[length] = ptr.val;
            length--;
            ptr = ptr.next;
        }
        return ans;
    }
}
```