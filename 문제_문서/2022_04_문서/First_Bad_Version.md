###   정답(Solution)
```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        
        int mid, bot = 1, top = n;
        
        while(bot <= top){
            mid = bot + (top - bot) / 2;
            if(isBadVersion(mid)) top = mid - 1;
            else bot = mid + 1;
        }
        return bot;
    }
}
```

###   분석
-   이진탐색