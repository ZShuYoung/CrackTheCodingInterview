## 思路

1. DFS + 回溯
2. DFS：从没一点开始向四周扩散，循环结束的条件是到达边界或者不匹配
3. 回溯：因为要每个点只能遍历一次，所以访问之后把点置为'/' 再做DFS，DFS结束后恢复

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        if(board==null || board.length==0){
            return false;
        }
        for(int i=0; i<board.length; i++){
            for(int j=0; j<board[0].length; j++){
                if(dfs(board, i, j, 0, word)){
                    return true;
                }
            }
        }
        return false;
    }

    private boolean dfs(char[][] board, int i, int j, int k, String word){
        if(i<0 || i>= board.length || j<0 || j>=board[0].length){
            return false;
        }
        if(board[i][j] != word.charAt(k)){
            return false;
        }
        // 先做校验之后，最后再判断k值
        if(k == word.length()-1){
            return true;
        }
        char temp = board[i][j];
        board[i][j] = '&';
        boolean ans = dfs(board, i-1, j, k+1, word) || dfs(board, i+1, j, k+1, word) || dfs(board, i, j-1, k+1, word) || dfs(board, i, j+1, k+1, word);
        board[i][j] = temp;
        return ans;
    }
}
```