```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        int k = n % s.length();
        String left = s.substring(0, k);
        String right = s.substring(k);
        return right+left;
    }
}
```