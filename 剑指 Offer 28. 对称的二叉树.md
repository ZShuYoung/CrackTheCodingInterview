## 思路

1. 递归

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root==null) return true;
        return helper(root.left, root.right);
    }

    private boolean helper(TreeNode left, TreeNode right){
        if(left == null && right == null){
            return true;
        }
        if(left == null ^ right == null){
            return false;
        }
        // left和right结点的值要判断
        return left.val == right.val && helper(left.right, right.left) && helper(left.left, right.right);
    }
}
```