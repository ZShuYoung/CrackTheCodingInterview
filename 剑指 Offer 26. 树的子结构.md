## 思路

1. 递归
2. 这里求的是B为A的子结构，子结构和子树有一点不同的是 `A!=null B==null` 这时候B属于A的子结构，这是个 `572. 另一个树的子树` 不同的地方

```java
class Solution {
    public boolean isSubStructure(TreeNode A, TreeNode B) {
        // 因为规定null不为任何树的子结构，所以这里返回null
        if(B==null) return false;
        if(A==null) return false;
        return isSameTree(A,B) || isSubStructure(A.left, B) || isSubStructure(A.right, B);
    }

    private boolean isSameTree(TreeNode A, TreeNode B) {
        if(A==null && B==null) return true;
        // A不为null 但是B为null对应下面的场景
        //    4             4
        //   / \           /
        //  1   2         1
        if(A!=null && B==null) return true;
        if(A==null && B!=null) return false;
        return A.val == B.val && isSameTree(A.left, B.left) && isSameTree(A.right, B.right);
    }
}
```

3. 对比下 `572. 另一个树的子树` 的代码
```java
class Solution {
    public boolean isSubtree(TreeNode A, TreeNode B) {
        // 这里null可以为任何树的子树
        if(B==null) return true;
        if(A==null) return false;
        return isSameTree(A,B) || isSubtree(A.left, B) || isSubtree(A.right, B);
    }

    private boolean isSameTree(TreeNode A, TreeNode B) {
        if(A==null && B==null) return true;
        if(A==null ^ B==null) return false;
        return A.val == B.val && isSameTree(A.left, B.left) && isSameTree(A.right, B.right);
    }
}
```