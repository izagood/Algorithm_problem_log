###   정답
```java
import java.util.*;
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        
        s = s.toLowerCase();
        s = s.replaceAll("[^py]", "");
        
        int p = 0;
        int y = 0;
        for(int i=0; i<s.length(); i++){
            if(s.charAt(i) == 'p'){
                p++;
            }else{
                y++;
            }
        }
        
        if(p != y){
            return false;
        }
        
        return answer;
    }
}
```

###   분석
-   문자열 기능을 알고 있는지 물어보는 문제

###   참고할 만한 정답
```java
class Solution {
    boolean solution(String s) {
        s = s.toUpperCase();

        return s.chars().filter( e -> 'P'== e).count() == s.chars().filter( e -> 'Y'== e).count();
    }
}
```

###   비교 분석
-   와... 스트링으로 IntStream으로 변환하는 함수가 있었다.
-   새로 알게된 내용이기는 하지만 공부했던것 처럼 wrapped type이 아닌 이상 성능 차이가 많이 발생한다.
-   List, Set, Map 등 wrapper type을 사용하는 경우만 되도록 stream을 쓰자