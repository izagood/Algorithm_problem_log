###   정답(Solution)

-   Hash Set

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        int len = board.length;
        
        HashSet<Character>[] row = new HashSet[len];
        HashSet<Character>[] col = new HashSet[len];
        HashSet<Character>[] box = new HashSet[len];

        for(int i=0; i<len; i++){
            row[i] = new HashSet<Character>();
            col[i] = new HashSet<Character>();
            box[i] = new HashSet<Character>();
        }
        
        for(int r=0; r<len; r++){
            for(int c=0; c<len; c++){
                char value = board[r][c];
                
                if(value == '.'){
                   continue; 
                }
                
                if(row[r].contains(value)){
                    return false;
                }
                row[r].add(value);
                
                if(col[c].contains(value)){
                    return false;
                    
                }
                col[c].add(value);
                
                int idx = (r/3) * 3 + c /3;
                if(box[idx].contains(value)){
                    return false;
                    
                }
                box[idx].add(value);
            }
        }
        return true;
        
    }
}
```

-   Array of Fixed Length

```java
    소스코드
```
-   Bitmasking

```java
    소스코드
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