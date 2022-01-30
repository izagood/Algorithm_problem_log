##   문제1
-   문제 링크 : [Keep Multiplying Found Values by Two](https://leetcode.com/contest/weekly-contest-278/problems/keep-multiplying-found-values-by-two/)
####    정답
```java
import java.util.*;

class Solution {
    public int findFinalValue(int[] nums, int original) {
        Arrays.sort(nums);
        while(Arrays.binarySearch(nums, original) >= 0){
            original *= 2;
        }
        return original;
    }
}
```

####    분석
-   sort

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int findFinalValue(int[] nums, int original) {
        Set<Integer> set = new HashSet<>();
        for(int u : nums)set.add(u);
        while(set.contains(original)){
            original *= 2;
        }
        return original;
    }
}
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제2
-   문제 링크 : \[문제명\]\(링크\)
####    정답
```java
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
-   문제 링크 : \[문제명\]\(링크\)
####    정답
```java
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


##   문제4
-   문제 링크 : \[문제명\]\(링크\)
####    정답
```java
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