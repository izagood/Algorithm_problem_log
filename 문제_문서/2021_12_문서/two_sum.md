#   정답
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        //a + b 했을때 타겟을 만드는 코드
        
        int loop = nums.length;
        
        int[] answer = new int[2];
        
        //먼저 for문 돌면서 하나씩 하면 되네
        for(int index1 = 0; index1 < loop; index1++){
            for(int index2 = index1 + 1; index2 < loop; index2++){
                if(nums[index1] + nums[index2] == target){
                    
                    answer[0] = index1;
                    answer[1] = index2;
                    
                    return answer;
                }
            }
        }
        
        
        return answer;
        
    }
}
```