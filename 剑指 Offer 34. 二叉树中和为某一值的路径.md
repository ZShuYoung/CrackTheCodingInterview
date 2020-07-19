```java
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> ans = new LinkedList<>();
        if(root==null){
            return ans;
        }
        List<Integer> one = new LinkedList<>();
        backTrack(ans, one, root, sum);
        return ans;
    }

    private void backTrack(List<List<Integer>> ans, List<Integer> one, TreeNode root, int sum){
        if(root==null) return;
        // 这里先加到数组再进行判断
        one.add(root.val);
        if(root.val==sum && root.left==null && root.right==null){
            ans.add(new LinkedList<Integer>(one));
        }else{
            backTrack(ans, one, root.left, sum-root.val);
            backTrack(ans, one, root.right, sum-root.val);
        }
        // 最后remove掉
        one.remove(one.size()-1);
    }
}
```