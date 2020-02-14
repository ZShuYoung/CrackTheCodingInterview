## 思路
- 和32-2思路一样，这里多加了一个反转标志位

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
        boolean reverseFlag = false;
        while(!q.isEmpty()){
            List<Integer> level = new LinkedList<>();
            int levelNodeNumber = q.size();
            for(int i=0; i<levelNodeNumber; i++){
                cur = q.poll();
                if(reverseFlag){
                    level.add(0, cur.val);
                }else{
                    level.add(cur.val);
                }
                if(cur.left!=null){
                    q.add(cur.left);
                }
                if(cur.right!=null){
                    q.add(cur.right);
                }
            }
            reverseFlag = !reverseFlag;
            ans.add(level);
        }
        return ans;
    }
}
```