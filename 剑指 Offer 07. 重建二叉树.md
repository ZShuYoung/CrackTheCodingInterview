## 思路

1. 递归，root必然是preorder的第一个数
2. 在inorder中找出root值所在的index，那么左半边为左子树 右半边为右子树。结合图分析

```
preorder   ○□□□×××
inorder    □□□○×××
              ↑
            index
```

```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length==0 || inorder.length==0){
            return null;
        }
        return helper(preorder, 0, preorder.length-1, inorder, 0, inorder.length-1);
    }

    private TreeNode helper(int[] preorder, int preStart, int preEnd, int[] inorder, int inStart, int inEnd) {
        if(preStart > preEnd){
            return null;
        }
        if(preStart == preEnd){
            return new TreeNode(preorder[preStart]);
        }
        TreeNode root = new TreeNode(preorder[preStart]);
        int index = -1;
        for(int i=0; i<inorder.length;i++){
            if(inorder[i] == root.val){
                index = i;
                break;
            }
        }
        root.left = helper(preorder, preStart+1, index, inorder, inStart, index-1);
        root.right = helper(preorder, index+1, preEnd, inorder, index+1, inEnd);
        return root;
    }
}
```