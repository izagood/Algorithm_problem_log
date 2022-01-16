##  문제1
-   문제 링크 : [Check if Every Row and Column Contains All Numbers](https://leetcode.com/contest/weekly-contest-275/problems/check-if-every-row-and-column-contains-all-numbers/)

####    정답
```java
import java.util.*;
class Solution {
    public boolean checkValid(int[][] matrix) {
        /*
            행열에 n까지 있는지.
            행열에 대해서 각각
            행
            열
            유효성 체크를 어떻게?
        */
        int len = matrix.length;
        List<Integer> list = new ArrayList<>();
        for(int i=1; i<=len; i++){
            list.add(i);
        }
        for(int i=0; i<len; i++){//행
        List<Integer> list2 = new ArrayList<>();
            for(int j=0; j<len; j++){
                list2.add(matrix[i][j]);
            }
            for(int k=0; k<len; k++){
                if(!list2.contains(list.get(k))){
                    return false;
                }
            }
        }
        for(int i=0; i<len; i++){//열
        List<Integer> list3 = new ArrayList<>();
            for(int j=0; j<len; j++){
                list3.add(matrix[j][i]);
            }
            for(int k=0; k<len; k++){
                if(!list3.contains(list.get(k))){
                    return false;
                }
            }
        }
        return true;
    }
}
```

####    분석

####    참고할 만한 정답
```java
class Solution {
    public boolean checkValid(int[][] matrix) {
        int[][] a = matrix;
        int n = matrix.length;
        for(int i = 0;i < n;i++){
			Set<Integer> set = new HashSet<>();
			for(int j = 0;j < n;j++){
				set.add(a[i][j]);
			}
			if(set.size() != n)return false;
		}
		for(int i = 0;i < n;i++){
			Set<Integer> set = new HashSet<>();
			for(int j = 0;j < n;j++){
				set.add(a[j][i]);
			}
			if(set.size() != n)return false;
		}
        return true;
    }
}
```

##  문제2
-   문제 링크 : [Minimum Swaps to Group All 1's Together II](https://leetcode.com/contest/weekly-contest-275/problems/minimum-swaps-to-group-all-1s-together-ii/)

####    정답
```java
```

####    분석
####    참고할 만한 정답
```java
class Solution {
    public int minSwaps(int[] a) {
        int n = a.length;
        int[] cum = new int[2*n+1];
        for(int i = 0;i < 2*n;i++){
            cum[i+1] = cum[i] + a[i%n];
        }
        int o = cum[n];
        int max = 0;
        for(int i = 0;i < n;i++){
            max = Math.max(max, cum[i+o] - cum[i]);
        }
        return o - max;
    }
}
```


##  문제3
-   문제 링크 : [Count Words Obtained After Adding a Letter](https://leetcode.com/contest/weekly-contest-275/problems/count-words-obtained-after-adding-a-letter/)
####    정답
-   시간초과

####    분석
####    참고할 만한 정답
```java
class Solution {
    public int wordCount(String[] startWords, String[] targetWords) {
        Set<Integer> set = new HashSet<>();
        for(String s: startWords){
            int ptn = 0;
            for(char c : s.toCharArray()){
                ptn |= 1<<c-'a';
            }
            set.add(ptn);
        }
        int ret = 0;
        outer:
        for(String t : targetWords){
            int ptn = 0;
            for(char c : t.toCharArray()){
                ptn |= 1<<c-'a';
            }
            for(int i = 0;i < 26;i++){
                if(ptn<<~i<0 && set.contains(ptn^1<<i)){
                    ret++;
                    continue outer;
                }
            }
        }
        return ret;
    }
}
```


##  문제4
-   문제 링크 : [Earliest Possible Day of Full Bloom](https://leetcode.com/contest/weekly-contest-275/problems/earliest-possible-day-of-full-bloom/)
####    정답
-   시간초과

####    분석
####    참고할 만한 정답
```java
class Solution {
    public int earliestFullBloom(int[] plantTime, int[] growTime) {
        // max(pi+gi,pi+pj+gj) < max(pj+gj,pi+pj+gi)
        // pi+pj+gj < pi+pj+gi
        int n = plantTime.length;
        int[][] a = new int[n][];
        for(int i = 0;i < n;i++){
            a[i] = new int[]{plantTime[i], growTime[i]};
        }
        Arrays.sort(a, (x, y) -> -(x[1] - y[1]));
        int ans = 0;
        int time = 0;
        for(int[] u : a){
            ans = Math.max(ans, time + u[0] + u[1]);
            time += u[0];
        }
        return ans;
    }
}
```