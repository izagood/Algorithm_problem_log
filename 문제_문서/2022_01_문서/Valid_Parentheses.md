#   정답
```java
import java.util.*;

class Solution {
    public boolean isValid(String s) {
        
        /*
            (){}[]
            열리고 같은걸로 닫혀야한다.
            올바른 순서로 닫혀야한다.
        */
        
        //Stack
        
        
        Stack<String> st = new Stack<>();
        Map<String, String> map = new HashMap<>();
        map.put("(", ")");
        map.put("{", "}");
        map.put("[", "]");
        
        //첫번째는 그냥 넣는다.
        st.push(String.valueOf(s.charAt(0)));
        
        //스택에 넣고
        int length = s.length();
        for(int i=1; i<length; i++){
            String str = String.valueOf(s.charAt(i));
            if(i-1 >= 0){
                if(st.empty() == false && str.equals(map.get(st.peek()))){
                    st.pop();
                }else{
                    st.push(str);
                }
            }
        }
        System.out.println(st);
        
        return st.empty();
        
    }
}
```

#   분석
-   Stack을 사용할 줄 아는지 묻는 문제

#   참고할 만한 정답
-   charAt을 사용하지 않고 substring에 index를 사용해서 하나씩 가져올 수 있다.
-   시작되는 괄호이면 push 아니면 비교하여 pop하는 방식

```java
class Solution {
    public boolean isValid(String s) {
        Stack<String> stk = new Stack<>();
       for(int i = 0; i < s.length(); i++){
            String c = s.substring(i, i+1);
            if(c.equals("(") || c.equals("{")  || c.equals("[") ) stk.push(c);
            else if(!stk.isEmpty()) {
                if(stk.peek().equals("(") && c.equals(")")) stk.pop();
                else if(stk.peek().equals("[") && c.equals("]")) stk.pop();
                else if(stk.peek().equals("{") && c.equals("}")) stk.pop();
                else return false;
            }
            else return false;
        }
        return stk.isEmpty();
    }
}
```