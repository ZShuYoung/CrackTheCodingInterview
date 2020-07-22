## 思路

1. 基于快排的思路，不断求partition的返回结果，当partition==k-1的时候，那面前k个数字必然是最小的k个

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if(arr.length==0 || k==0) return new int[]{};
        int l=0, r=arr.length-1;
        while(true){
            int partitionIndex = partition(arr, l, r);
            if(partitionIndex == k-1){
                return Arrays.copyOfRange(arr, 0, k);
            }else if(partitionIndex < k-1){
                l = partitionIndex+1;
            }else{
                r = partitionIndex-1;
            }
        }
    }

    private int partition(int[] arr, int l, int r){
        int rr = r;
        int povit = arr[r];
        while(l < r){
            while(l<r && arr[l]<=povit){
                l++;
            }

            while(l<r && arr[r]>=povit){
                r--;
            }

            if(l<r){
                swap(arr, l, r);
            }
        }
        swap(arr, l, rr);
        return l;
    }

    private void swap(int[] arr, int i, int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```