###   정답(Solution)

-   Hash Map

```java
import java.util.*;
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        if(nums1.length > nums2.length) return intersect(nums2, nums1);
        
        Map<Integer, Integer> map = new HashMap<>();
        for(int n : nums1){
            map.put(n, map.getOrDefault(n, 0)+1);
        }
        int k = 0;
        for(int n : nums2){
            int cnt = map.getOrDefault(n, 0);
            if(cnt > 0){
                nums1[k++] = n;
                map.put(n, cnt -1);
            }
        }
        return Arrays.copyOfRange(nums1, 0, k);
    }
}
```

###   분석


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