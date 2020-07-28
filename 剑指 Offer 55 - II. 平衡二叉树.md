## 思路

1. 一棵树是平衡二叉树的充分条件为：`根节点左右子树高度差不超过1，并且根节点的左右子树也都是平衡二叉树`。所以很容易写出递归代码。

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        if(root==null) return true;
        int leftDepth = getDepth(root.left);
        int rightDepth = getDepth(root.right);
        if(Math.abs(leftDepth-rightDepth)>1){
            return false;
        }
        return isBalanced(root.left) && isBalanced(root.right);
    }

    private int getDepth(TreeNode root){
        if(root==null) return 0;
        return Math.max(getDepth(root.left), getDepth(root.right)) + 1;
    }
}
```