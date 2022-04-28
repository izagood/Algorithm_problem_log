###   정답(Solution)
```java
class Solution {
    public int search(int[] nums, int target) {
        int bot = 0, mid, top = nums.length - 1;
        while(bot <= top){
            mid = bot + (top - bot) / 2;
            if(nums[mid] == target) return mid;
            if(nums[mid] < target) bot = mid + 1;
            else top = mid - 1;
        }
        return -1;
    }
}
```

###   분석
-   이진탐색