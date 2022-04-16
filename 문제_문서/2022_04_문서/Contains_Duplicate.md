###   정답(Solution)
```java
import java.util.*;
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for(int i=0; i<nums.length - 1; i++){
            if(nums[i] == nums[i + 1]) return true;
        }
        return false;
    }
}
```

###   분석
-   2중 for문으로 찾을 경우 O(N2)이 되므로 시간 초과가 된다.
-   정렬하고 하나의 위치씩 비교 하여 O(N)으로 풀이 하여야 한다.