###   정답(Solution)

-   이중 for문 풀이 (시간 초과)

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

-   DP 풀이

```java
class Solution {
    public int maxSubArray(int[] nums) {

        int currentSubarray = nums[0];
        int maxSubarray = nums[0];
        
        for (int i = 1; i < nums.length; i++) {
            int num = nums[i];

            currentSubarray = Math.max(num, currentSubarray + num);
            maxSubarray = Math.max(maxSubarray, currentSubarray);
        }
        
        return maxSubarray;
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