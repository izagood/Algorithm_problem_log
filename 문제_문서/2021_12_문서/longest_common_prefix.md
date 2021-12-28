#   정답
```java

class Solution {
    public String longestCommonPrefix(String[] strs) {
        /*
            공통 prefix를 리턴 없으면 ""
        */
        if(strs.length == 1){
            return strs[0];
        }
        for(String str:strs){
            if("".equals(str)){
                return "";
            }
        }
        
        String prefix = "";
        
        //각 단어를 하나씩 비교하면서 가야함.
        // flower flow flight
        // f f f
        // l l l
        // o o i -> 팅겨
        int wordIdx = 0;
        int charIdx = 0;
        for(;;){
            if(!strs[wordIdx].equals("")){
                System.out.println(wordIdx);
                int nowLength = strs[wordIdx].length();
                if(charIdx > nowLength - 1){
                    break;
                }
                char now = strs[wordIdx].charAt(charIdx);
                if(wordIdx+1 < strs.length && !strs[wordIdx+1].equals("")){
                    int nextLength = strs[wordIdx+1].length();
                    if(charIdx > nextLength - 1){
                        break;
                    }
                    char next = strs[wordIdx+1].charAt(charIdx);
                    if(now != next){
                        break;
                    }
                    wordIdx++;
                }else{
                    prefix += String.valueOf(strs[wordIdx].charAt(charIdx));
                    wordIdx = 0;
                    charIdx++;
                }
            }else{
                return "";
            }
        }
        
        
        
        return prefix;
    }
}

```


#   분석
-   풀이는 했는데 너무 간결하지 못한 풀이임
-   좀 더 간결한 정답으로 리펙토링

#   참고할 만한 정답
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
    //arr가 없을때는 ""
    if (strs.length == 0){
        return "";
    }

    //첫번째 단어를 prefix로
    String prefix = strs[0];

    //2번째 단어부터 for
    for (int i = 1; i < strs.length; i++){
        //prefix의 indexOf가 0이 아닌 경우 while
        while (strs[i].indexOf(prefix) != 0) {
            //prefix를 한글자씩 줄인다.
            prefix = prefix.substring(0, prefix.length() - 1);
            //prefix가 없는 경우 ""
            if (prefix.isEmpty()){
                return "";
            }
        }        
    }
    return prefix;
    }
}
```