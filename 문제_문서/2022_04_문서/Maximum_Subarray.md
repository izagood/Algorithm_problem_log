###   정답(Solution)

-   이중 for문 (시간 초과)

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        
        for(int i=0; i<nums.length; i++){
            int currMax = 0;
            for(int j=i; j<nums.length; j++){
                currMax += nums[j];
                max = Math.max(max, currMax);
            }
        }
        return max;
    }
}
```

-   

```java

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