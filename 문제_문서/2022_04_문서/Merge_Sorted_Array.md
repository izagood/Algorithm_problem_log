###   정답(Solution)

-   일반적인 방법

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        for(int i=0; i<n; i++){
            nums1[i+m] = nums2[i];
        }
        Arrays.sort(nums1);
    }
}
```

###   분석
-   시간복잡도 : O((n+m)log(n+m))



-   three pointers

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = m - 1, p2 = n - 1;
        for(int p = m + n - 1; p >= 0; p--){
            if(p2 < 0) break;
            if(p1 >= 0 && nums1[p1] > nums2[p2]) nums1[p] = nums1[p1--];
            else nums1[p] = nums2[p2--];
        }
    }
}
```

###   분석
-   시간복잡도 : O(n+m)

###   참고할 만한 정답
```java
    소스코드
```

###   비교 분석
-   비교 분석한 내용

###   비교 분석 반영
```java
    정답에 참고한 내용 추가
```