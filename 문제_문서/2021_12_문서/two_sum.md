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

###   분석
-   타겟을 찾기 위해 이중 for문 ( O(N^2) )으로 풀었다.

###   참고할 만한 정답
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
                return new int[] {i, map.get(target - nums[i])};
            }
            
            map.put(nums[i], i);
        }
        
        return new int[0];
    }
}
```

###   비교 분석
-   HashMap은 O(1)이고 for문은 O(N)이므로 위 방법으로 풀면 O(N)으로 풀 수 있다.
-   더해서 target을 찾는 것이 아니라 target에서 nums[]의 값을 빼서 map에 key 값으로 존재하는지 찾는다.
-   map.containsKey() 함수가 포인트

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {

        Map<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {

            if (map.containsKey(target - nums[i])) {
                return new int[] {i, map.get(target - nums[i])};
            }
            
            map.put(nums[i], i);
        }
        
        return new int[0];
    }
}
```