## 思路

1. 第一个只出现一次的字符，必然需要遍历整个字符串，因为不遍历到最后并不能知道字符c是否只出现了一次
2. 用一个数组保存每个字符出现的次数
3. 第二次遍历字符串，一旦出现其次数为1的则返回
4. 如果第二次遍历结束了还没返回说明不存在，就返回空

```java
class Solution {
    public char firstUniqChar(String s) {
        int[] idx = new int[26];
        for(char c : s.toCharArray()){
            idx[ c - 'a']++;
        }
        for(char c : s.toCharArray()){
            if(idx[ c - 'a'] == 1){
                return c;
            }
        }
        return ' ';
    }
}
```