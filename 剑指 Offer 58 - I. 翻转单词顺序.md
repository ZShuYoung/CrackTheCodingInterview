```java
class Solution {
    public String reverseWords(String s) {
        StringBuilder sb = new StringBuilder();
        char[] chars = s.toCharArray();
        for(int i=0; i<chars.length; i++){
            if(chars[i]==' '){
                continue;
            }
            StringBuilder oneWord = new StringBuilder();
            while(i<chars.length && chars[i]!=' '){
                oneWord.append(chars[i]);
                i++;
            }
            sb.append(oneWord.reverse().toString()).append(" ");
        }
        return sb.reverse().toString().trim();
    }
}
```