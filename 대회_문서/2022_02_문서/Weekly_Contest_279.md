##   문제1
-   문제 링크 : [Sort Even and Odd Indices Independently](https://leetcode.com/contest/weekly-contest-279/problems/sort-even-and-odd-indices-independently/)
####    정답
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int[] sortEvenOdd(int[] nums) {
        
        int len = nums.length;
        
        List<Integer> odd = new ArrayList<>();
        List<Integer> even = new ArrayList<>();
        
        for(int i=0; i<len; i++){
            if(i % 2 == 0){
                even.add(nums[i]);
            }else{
                odd.add(nums[i]);
            }
        }
        
        int[] eArr = even.stream().sorted().mapToInt(Integer::intValue).toArray();
        int eIdx = 0;
        
        int[] oArr = odd.stream().sorted(Comparator.reverseOrder()).mapToInt(Integer::intValue).toArray();
        int oIdx = 0;
        
        int[] a = new int[len];
        
        for(int i=0; i<len; i++){
            if(i % 2 == 0 ){
                a[i] = eArr[eIdx];
                eIdx++;
            }else{
                a[i] = oArr[oIdx];
                oIdx++;
            }
        }
        
        return a;
        
    }
}
```

####    분석
-   

####    참고할 만한 정답
```java
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제2
-   문제 링크 : [Smallest Value of the Rearranged Number](https://leetcode.com/contest/weekly-contest-279/problems/smallest-value-of-the-rearranged-number/)
####    정답
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public long smallestNumber(long num) {
        
        if(String.valueOf(num).length() == 1){
            return num;
        }
        
        String str = "";
        boolean p = true;
        
        if(num < 0){
            str = String.valueOf(num).substring(1);
            p = false;
        }else{
            str = String.valueOf(num);
        }
        
        String[] arr = str.split("");
        
        
        int zCnt = 0;
            
        if(p){
            Arrays.sort(arr);
            for(String str1 : arr){
                if(str1.equals("0")){
                    zCnt++;
                }else{
                    break;
                }
            }
        }else{
            Arrays.sort(arr, Comparator.reverseOrder());
        }
        
        
        
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<arr.length; i++){
            sb.append(arr[i]);
        }
        
        if(p){
            String temp = sb.toString();
            
            String t1 = temp.substring(0, zCnt);
            String t2 = temp.substring(zCnt, zCnt+1);
            String t3 = temp.substring(zCnt+1);
            
            temp = t2 + t1 + t3;
            return Long.valueOf(temp);
        }else{
            String temp = sb.toString();
            temp = "-" + temp;
            return Long.valueOf(temp);
        }
    }
}
```

####    분석
-   

####    참고할 만한 정답
```java
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제3
-   문제 링크 : [Design Bitset](https://leetcode.com/contest/weekly-contest-279/problems/design-bitset/)
####    정답
-   풀이 못 함

####    분석
-   

####    참고할 만한 정답
```java
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제4
-   문제 링크 : [Minimum Time to Remove All Cars Containing Illegal Goods](https://leetcode.com/contest/weekly-contest-279/problems/minimum-time-to-remove-all-cars-containing-illegal-goods/)
####    정답
-   풀이 못 함

####    분석
-   

####    참고할 만한 정답
```java
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```