## 思路

```
以下面这棵树为例：
     4
   /   \
  2     7
 / \   / \
1   3 6   9 

    ↓↓

     4
   /   \
  7     2
 / \   / \
9   6 3   1

单独看原来的左子树实际上也自己翻转成
  2            2     
 / \          / \ 
1   3        3   1

所以基本就是:左子树自身翻转后变成了右子树
```

```java
class Solution {
    public TreeNode mirrorTree(TreeNode root) {
        if(root==null) return null;
        TreeNode mirrorLeft = mirrorTree(root.right);
        TreeNode mirrorright = mirrorTree(root.left);
        root.left = mirrorLeft;
        root.right = mirrorright;
        return root;
    }
}
```