## 思路

1. 考虑到要把二叉搜索树转换成排序的双向链表，那么又因为二叉搜索树的中序遍历实际上就是顺序的，所以往中序遍历上考虑
2. 考虑如下传统的递归中序遍历，实际上打印出来的顺序就是顺序的。那么我们改写 `System.out.println(cur.val);` 这一块的逻辑
3. 使用 `head` 表示头部， 使用 `pre` 表示前一个Node

```java
private void dfs(Node cur){
        if(cur==null) return;
        dfs(cur.left);
        System.out.println(cur.val);
        dfs(cur.right);
    }
```

```java
class Solution {
    private Node head, pre;
    public Node treeToDoublyList(Node root) {
        if(root==null){
            return null;
        }
        dfs(root);
        // 最后头尾两个Node也连接起来
        head.left = pre;
        pre.right = head;
        return head;
    }

    private void dfs(Node cur){
        if(cur==null) return;
        dfs(cur.left);

        // 递归到值最小的Node了，这时候如果pre==null 说明当前为head，这里标记一下
        // 否则的话就把pre和cur连接起来
        if(pre==null){
            head = cur;
        }else{
            pre.right = cur;
            cur.left = pre;
        }
        // pre重新指向cur
        pre = cur;

        dfs(cur.right);
    }
}
```