## 思路 

1. 定义一种先右子树的中序遍历

```java
class Solution {
    public int kthLargest(TreeNode root, int k) {
        Deque<TreeNode> stack = new ArrayDeque<>();
        TreeNode cur = root;
        while(!stack.isEmpty() || cur != null){
            while(cur!=null){
                stack.push(cur);
                cur=cur.right;
            }
            if(k==1){
                return stack.pop().val;
            }
            cur = stack.pop().left;
            k--;
        }
        return 0;
    }
}
```