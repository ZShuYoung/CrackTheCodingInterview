## 思路

1. 先把`int[]`转成`string[]`，然后自定义一个Comparator对string[]进行排序。
2. 自义定Comparator的规则是String按照字典顺序排序
3. 举个例子 "30" "3"可以组成"303"和"330"，按照字典顺序应该是"303"

```java
class Solution {
    public String minNumber(int[] nums) {
        String[] temp = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            temp[i] = String.valueOf(nums[i]);
        }
        // 关键就是这一步
        Arrays.sort(temp, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return (o1 + o2).compareTo(o2 + o1);
            }
        });
        StringBuilder sb = new StringBuilder();
        for (String s : temp) {
            sb.append(s);
        }
        return sb.toString();

    }
}
```