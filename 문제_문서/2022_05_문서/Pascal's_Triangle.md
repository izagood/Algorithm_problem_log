###   정답(Solution)
```java
import java.util.*;
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> answer = new ArrayList<List<Integer>>();
        
        answer.add(new ArrayList<>());
        answer.get(0).add(1);
        
        for(int i=1; i<numRows; i++){
            List<Integer> row = new ArrayList<>();
            List<Integer> preRow = answer.get(i-1);
            
            row.add(1);
            
            for(int j=1; j<i; j++){
                row.add(preRow.get(j-1) + preRow.get(j));
            }
            
            row.add(1);
            
            answer.add(row);
        }
        return answer;
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