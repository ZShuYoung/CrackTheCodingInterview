```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> ans = new LinkedList<>();
        if(root==null){
            return ans;
        }
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        TreeNode cur;
        while(!q.isEmpty()){
            List<Integer> level = new LinkedList<>();
            int levelNodeNumber = q.size();
            for(int i=0; i<levelNodeNumber; i++){
                cur = q.poll();
                level.add(cur.val);
                if(cur.left!=null){
                    q.add(cur.left);
                }
                if(cur.right!=null){
                    q.add(cur.right);
                }
            }
            ans.add(level);
        }
        return ans;
    }
}
```