#   정답
```java
import java.util.*;

class Solution {
    public int romanToInt(String s) {
        
        /*
            String arr 로 만들고 하나씩 빼면서 이후에 VX LC DM 이 오는지 체크하면서 교체
            IV, IX, XL , XC, CD, CM
        */
        
        Map<String, Integer> romanMap = new HashMap<>();
        romanMap.put("I", 1);
        romanMap.put("V", 5);
        romanMap.put("X", 10);
        romanMap.put("L", 50);
        romanMap.put("C", 100);
        romanMap.put("D", 500);
        romanMap.put("M", 1000);
        
        int sum = 0;
        
        String[] arr = s.split("");
        String now = "";
        String post = "";
        
        for(int i=0; i<arr.length; i++){
            now = arr[i];
            System.out.println(now);
            
            if(i+1 < arr.length){
                post = arr[i+1];
                
                if("I".equals(now) && "V".equals(post)){
                    sum += 4;
                    i++;
                }else if("I".equals(now) && "X".equals(post)){
                    sum += 9;
                    i++;
                }else if("X".equals(now) && "L".equals(post)){
                    sum += 40;
                    i++;
                }else if("X".equals(now) && "C".equals(post)){
                    sum += 90;
                    i++;
                }else if("C".equals(now) && "D".equals(post)){
                    sum += 400;
                    i++;
                }else if("C".equals(now) && "M".equals(post)){
                    sum += 900;
                    i++;
                }else{
                    sum += romanMap.get(now);
                }
            }else{
                sum += romanMap.get(now);
            }
            System.out.println(sum);
        }
        
        return sum;
    }
}


```

#   분석
-   map을 이용해서 해당 숫자를 더 해주면 된다.
-   문자 2개가 숫자 1개로 변환될때는 i에 +1을 해준다.

