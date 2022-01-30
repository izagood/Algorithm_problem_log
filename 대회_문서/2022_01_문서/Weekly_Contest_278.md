##   문제1
-   문제 링크 : [Keep Multiplying Found Values by Two](https://leetcode.com/contest/weekly-contest-278/problems/keep-multiplying-found-values-by-two/)
####    정답
```java
import java.util.*;

class Solution {
    public int findFinalValue(int[] nums, int original) {
        Arrays.sort(nums);
        while(Arrays.binarySearch(nums, original) >= 0){
            original *= 2;
        }
        return original;
    }
}
```

####    분석
-   sort

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int findFinalValue(int[] nums, int original) {
        Set<Integer> set = new HashSet<>();
        for(int u : nums)set.add(u);
        while(set.contains(original)){
            original *= 2;
        }
        return original;
    }
}
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제2
-   문제 링크 : [All Divisions With the Highest Score of a Binary Array](https://leetcode.com/contest/weekly-contest-278/problems/all-divisions-with-the-highest-score-of-a-binary-array/)

####    정답 (시간초과)
```java
import java.util.*;

class Solution {
    public List<Integer> maxScoreIndices(int[] nums) {
        
        int[] arr = new int[nums.length + 1];
        
        for(int i=0; i<=nums.length; i++){
            arr[i] = div(nums, i);
        }
        
        int max = Integer.MIN_VALUE;
        int tmax = Integer.MIN_VALUE;
        for(int i=0; i<arr.length; i++){
            if(i+1 < arr.length){
                tmax = Math.max(arr[i], arr[i+1]);
                if(max < tmax){
                    max = tmax;
                }
            }
        }
        
        List<Integer> ilist = new ArrayList<>();
        for(int i=0; i<arr.length; i++){
            if(arr[i] == max){
                ilist.add(i);
            }
        }
        
        return ilist;
    }
    
    private int div(int[] nums, int idx){
        
        int[] l = new int[idx];
        int[] r = new int[nums.length - idx];
        
        int lidx = 0;
        int ridx = 0;
        for(int i=0; i<nums.length; i++){
            if(i <= idx - 1){
                l[lidx] = nums[i];                
                lidx++;
            }else{
                r[ridx] = nums[i];
                ridx++;
            }
        }
        
        int lsum = 0;
        for(int n : l){
            if(n == 0){
                lsum++;
            }
        }
        
        int rsum = 0;
        for(int n : r){
            if(n == 1){
                rsum++;
            }
        }
        
        return lsum + rsum;
    }
}
```

####    분석
-   

####    참고할 만한 정답
```java
class Solution {
    public List<Integer> maxScoreIndices(int[] nums) {
        int s = 0;
        for(int u : nums){
            s += u;
        }
        List<Integer> can = new ArrayList<>();
        int max = s;
        can.add(0);
        int n = nums.length;
        for(int i = 1;i <= n;i++){
            if(nums[i-1] == 1)s--;
            if(nums[i-1] == 0)s++;
            if(s > max){
                max = s;
                can.clear();
                can.add(i);
            }else if(s == max){
                can.add(i);
            }
        }
        return can;
    }
}
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제3
-   문제 링크 : [Find Substring With Given Hash Value](https://leetcode.com/contest/weekly-contest-278/problems/find-substring-with-given-hash-value/)
####    미완성 풀이
```java
class Solution {
    public String subStrHash(String s, int power, int modulo, int k, int hashValue) {
        for(int i=0; i<s.length(); i++){
            if(i+k < s.length()){
                String sub = s.substring(i, i+k);
                if(valF(sub, power, k) % modulo == hashValue){
                    System.out.println(sub);
                    return sub;
                }
            }
        }
        return null;
    }
    
    //hash(s, p, m) = (val(s[0]) * p0 + val(s[1]) * p1 + ... + val(s[k-1]) * pk-1) mod m.
    
    private int valF(String s, int power, int k){
        
        int sum = 0;
        
        for(int i=0; i<s.length(); i++){
            int val = (int)s.charAt(i);
            int p = (int)Math.pow((double)power, (double)i);
            
            sum = sum + (val * p);
        }
        
        return sum;
    }
}
```

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public String subStrHash(String t, int power, int mod, int k, int hashValue) {
        char[] s = t.toCharArray();
        int n = s.length;
        long h = 0;
        int first = n;
        long pk = 1;
        for(int i = 0;i < k-1;i++){
            pk = pk * power % mod;
        }
        for(int i = n-1;i >= 0;i--){
            h = (h * power + (s[i]-'a'+1)) % mod;
            if(i <= n-k){
                if(h == hashValue){
                    first = i;
                }
                h = (h - pk * (s[i+k-1]-'a'+1)) % mod;
					if(h < 0)h += mod;
            }
        }
        return t.substring(first, first + k);
    }
}
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제4
-   문제 링크 : [Groups of Strings](https://leetcode.com/contest/weekly-contest-278/problems/groups-of-strings/)
####    시간초과

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int[] groupStrings(String[] words) {
        int n = words.length;
        int[] a = new int[n];
        DJSet ds = new DJSet(n);
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0;i < n;i++){
            for(char c : words[i].toCharArray()){
                a[i] |= 1<<c-'a';
            }
            if(map.containsKey(a[i])){
                ds.union(i, map.get(a[i]));
            }

            map.put(a[i], i);
        }

        for(int i = 0;i < n;i++){
            for(int j = 0;j < 26;j++){
                int k = a[i]^1<<j;
                if(map.containsKey(k)){
                    ds.union(i, map.get(k));
                }
            }
            for(int j = 0;j < 26;j++){
                for(int l = 0;l < 26;l++){
                    if(a[i]<<~j<0 && a[i]<<~l>=0){
                        int k = a[i]^1<<j^1<<l;
                        if(map.containsKey(k)){
                            ds.union(i, map.get(k));
                        }
                    }
                }
            }
        }

        int min = 0;
        for(int i = 0;i < n;i++){
            min = Math.min(min, ds.upper[i]);
        }
        int[] ans = new int[]{ds.count(), -min};
        return ans;
    }

    public class DJSet {
        public int[] upper;

        public DJSet(int n) {
            upper = new int[n];
            Arrays.fill(upper, -1);
        }

        public int root(int x) {
            return upper[x] < 0 ? x : (upper[x] = root(upper[x]));
        }

        public boolean equiv(int x, int y) {
            return root(x) == root(y);
        }

        public boolean union(int x, int y) {
            x = root(x);
            y = root(y);
            if (x != y) {
                if (upper[y] < upper[x]) {
                    int d = x;
                    x = y;
                    y = d;
                }
                upper[x] += upper[y];
                upper[y] = x;
            }
            return x == y;
        }

        public int count() {
            int ct = 0;
            for (int u : upper) if (u < 0) ct++;
            return ct;
        }

        public int[][] toBucket() {
            int n = upper.length;
            int[][] ret = new int[n][];
            int[] rp = new int[n];
            for (int i = 0; i < n; i++) if (upper[i] < 0) ret[i] = new int[-upper[i]];
            for (int i = 0; i < n; i++) {
                int r = root(i);
                ret[r][rp[r]++] = i;
            }
            return ret;
        }
    }

}
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```