###   정답(Solution)

####   일반적인 방법

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        for(int i=0; i<nums.length; i++){
            nums[i] = (int)Math.pow(Math.abs(nums[i]), 2);
        }
        Arrays.sort(nums);
        return nums;
    }
}
```

### 분석
-   시간 복잡도 : O(NlogN)

####   two pointer

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int len = nums.length;
        int[] ans = new int[len];
        int left = 0;
        int right = len - 1;
        for(int i=len-1; i>=0; i--){
            int num;
            if(Math.abs(nums[left]) < Math.abs(nums[right])){
                num = (int)Math.abs(nums[right]);
                right--;
            }else{
                num = (int)Math.abs(nums[left]);
                left++;
            }
            ans[i] = (int)Math.pow(num,2);
        }
        return ans;
    }
}
```

###   분석
-   시간 복잡도 : O(N)
-   two pointer : 2개의 포인터를 사용하는 방법이다.  
    기존에 정렬되어 있는 배열이 주어졌을때 사용할 수 있는 방법