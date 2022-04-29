###   정답(Solution)
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int mid, bot = 0, top = nums.length - 1;
        while(bot<=top){
            mid = bot + (top - bot) / 2;
            if(nums[mid] == target) return mid;
            if(nums[mid] < target) bot = mid + 1;
            else top = mid - 1;
        }
        return bot;
    }
}
```

###   분석
-   시간복잡도 O(log N) : 이진탐색
