## 思路

1. 二叉树层序遍历，使用队列来缓存各个结点

```java
class Solution {
    public int[] levelOrder(TreeNode root) {
        if(root==null){
            return new int[0];
        }
        List<Integer> list = new LinkedList<>();
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        TreeNode cur;
        while(!q.isEmpty()){
            cur = q.poll();
            list.add(cur.val);

            if(cur.left!=null){
                q.add(cur.left);
            }
            if(cur.right!=null){
                q.add(cur.right);
            }
        }
        int[] ans = new int[list.size()];
        for(int i=0; i<list.size(); i++){
            ans[i] = list.get(i);
        }
        return ans;
    }
}
```