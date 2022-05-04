###   정답(Solution)

-   풀이1

```java
class Solution {
    public int[][] matrixReshape(int[][] mat, int r, int c) {
        int[][] answer = new int[r][c];
        if (mat.length == 0 || r * c != mat.length * mat[0].length) return mat;
        
        int p1 = 0, p2 = 0;
        for(int i=0; i<mat.length; i++){
            for(int j=0; j<mat[i].length; j++){
                answer[p1][p2] = mat[i][j];
                p2++;
                if(p2 == c){
                    p1++;
                    p2 = 0;
                }
            }
        }
        return answer;
    }
}
```

###   분석

-   풀이2

```java
class Solution {
    public int[][] matrixReshape(int[][] mat, int r, int c) {
        int[][] answer = new int[r][c];
        if (mat.length == 0 || r * c != mat.length * mat[0].length) return mat;
        
        int cnt = 0;
        for(int i=0; i<mat.length; i++){
            for(int j=0; j<mat[i].length; j++){
                answer[cnt / c][cnt % c] = mat[i][j];
                cnt++;
            }
        }
        return answer;
    }
}
```
