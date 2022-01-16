##   문제1
-   문제링크 : [Divide a String Into Groups of Size k](https://leetcode.com/contest/weekly-contest-276/problems/divide-a-string-into-groups-of-size-k/)
####    정답
```java
class Solution {
    public String[] divideString(String s, int k, char fill) {
        int n = s.length();
        int g = n/k;
        int l = n%k > 0? 1 : 0;
        g += l;
        String[] a = new String[g];
        
        String[] sa = s.split("");
        int en = sa.length;
        int ec = 0;
        int c = 0;
        int gc = 0;
        String w = "";
        for(String ss : sa){
            ec++;
            c++;
            w += ss;
            if(c == k || ec == en){
                a[gc] = w;
                gc++;
                w = "";
                c = 0;
            }
        }
        
        if(l == 1){
            String ls = a[gc-1];
            int ln = a[gc-1].length();
            for(int i=0; i<k-ln; i++){
                ls += fill;
            }
            a[gc-1] = ls;
        }
        
        return a;
    }
}
```

####    분석
-   

####    참고할 만한 정답
```java
class Solution {
    public String[] divideString(String s, int k, char fill) {
        while(s.length() % k != 0){
            s += fill;
        }
        String[] ret = new String[s.length()/k];
        
        for(int i = 0;i < s.length()/k;i++){
            ret[i] = s.substring(i*k, (i+1)*k);
        }
        return ret;
    }
}
```


##   문제2
-   문제링크 : [Minimum Moves to Reach Target Score](https://leetcode.com/contest/weekly-contest-276/problems/minimum-moves-to-reach-target-score/)
####    정답
```java
class Solution {
    public int minMoves(int target, int maxDoubles) {
        int f = 1;
        int t = target;
        int m = maxDoubles;
        int a = 0;
        
        if(m == 0){
            a = t - f;
            return a;
        }
        
        while(t != f){
            if(t%2 == 0){
                if(m != 0){
                    t /= 2;
                    m--;
                    a++;
                }else{
                    int l = t - f;
                    return l + a;
                }
            }else{
                t = t-1;
                a++;
                if(m != 0){
                    t /= 2;
                    m--;
                    a++;
                }else{
                    int l = t - f;
                    return l + a;
                }
            }
        }
        
        return a;
        
    }
}
```

####    분석
-   초기값에서 target 점수에 최소 연산으로 도달하는 문제
-   역으로 target부터 초기값에 도달하는 최소 연산을 계산하였다.

####    참고할 만한 정답
```java
class Solution {
    public int minMoves(int target, int maxDoubles) {
        int ans = Integer.MAX_VALUE;
        for(int u = 0;u <= maxDoubles && u <= 30;u++){
            int rem = target - (1<<u);
            if(rem < 0)continue;
            int over = rem>>>u;
            
            ans = Math.min(ans, u + over + Integer.bitCount(rem-(over<<u)));
        }
        return ans;
    }
}
```

##   문제3
-   문제링크 : [Solving Questions With Brainpower](https://leetcode.com/contest/weekly-contest-276/problems/solving-questions-with-brainpower/)
####    정답
-   시간 초과

####    분석
-   만들 수 있는 가장 큰 점수

####    참고할 만한 정답
```java
class Solution {
    public long mostPoints(int[][] a) {
        int n = a.length;
        long[] dp = new long[n+1];
        for(int i = 0;i <= n;i++){
            if(i > 0)dp[i] = Math.max(dp[i], dp[i-1]);
            if(i < n){
                int ni = Math.min(n, i+a[i][1]+1);
                dp[ni] = Math.max(dp[ni], dp[i] + a[i][0]);
            }
        }
        return dp[n];
    }
}
```


##   문제4
-   문제링크 : [Maximum Running Time of N Computers](https://leetcode.com/contest/weekly-contest-276/problems/maximum-running-time-of-n-computers/)
####    정답
-   시간 초과

####    분석
-   최대한 규일하게 자원을 사용하는 문제

####    참고할 만한 정답
```java
class Solution {
    public long maxRunTime(int n, int[] b) {
        long low = -1, high = 100000000000007L;
        while(high - low > 1){
            long h = high+low>>1;
            long s = 0;
            for(int v : b){
                s += Math.min(v, h);
            }
            if(s >= n*h){
                low = h;
            }else{
                high = h;
            }
        }
        return low;
    }
}
```