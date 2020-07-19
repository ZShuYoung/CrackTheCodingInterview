## 思路

1. 结合二叉搜索树和后续遍历的特点，数组最后一个数必然是根结点
2. 从左开始找到第一个大于根结点的数，那么左半边即为左子树；然后遍历右半边的数，如果有小于根节点的，那必不可能是一个二叉搜索树
3. 循环结束条件是start>=end

```java
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        return helper(postorder, 0, postorder.length-1);
    }

    private boolean helper(int[] postorder, int start, int end){
        if(start>=end) return true;
        int root = postorder[end];
        // 这个idx即为右子树的开始下标，配合if(start>=end) return true初始化为end很有讲究
        int idx = end;
        for(int i=start; i<end; i++){
            if(postorder[i]>root){
                idx=i;
                break;
            }
        }
        for(int i=idx+1; i<end; i++){
            if(postorder[i]<root){
                return false;
            }
        }
        return helper(postorder, start, idx-1) && helper(postorder, idx, end-1);
    }
}
```