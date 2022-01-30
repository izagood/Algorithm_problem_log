###   정답
```java
import java.util.*;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        
        int num = commands.length;
        
        int[] answer = new int[num];
        
        //명령어 set만큼 돌면서 tempArr에 자른 배열을 담고 sort한다.
        int loop = 0;
        for(int[] command : commands){
            
            int startIndex = command[0] - 1;
            int endIndex = command[1];
            int kNum = command[2] - 1;
            
            int[] tempArr = Arrays.copyOfRange(array, startIndex, endIndex);
            Arrays.sort(tempArr);
            answer[loop] = tempArr[kNum];
            loop++;
        }
        
        return answer;
    }
}
```

###   분석
-   
-   알게된 함수 : Arrays.copyOfRange(배열, 시작인덱스(포함), 마지막인덱스(미포함));

-   사용 예시

```java
int[] array = {1, 5, 2, 6, 3, 7, 4};

int[] result = Arrays.copyOfRange(array, 2, 5);
//result = [2, 6, 3];
```
시작인덱스는 포함이여 2부터 출력되고
마지막인덱스는 미포함하여 3까지 출력된다.
