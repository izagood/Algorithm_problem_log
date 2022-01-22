##   문제1
-   문제 링크 : [Minimum Cost of Buying Candies With Discount](https://leetcode.com/contest/biweekly-contest-70/problems/minimum-cost-of-buying-candies-with-discount/)
####    정답 ⭕
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int minimumCost(int[] cost) {
        int a = 0;
        cost = Arrays.stream(cost).boxed().sorted(Comparator.reverseOrder()).mapToInt(Integer::intValue).toArray();
        
        int idx = 1;
        for(int i : cost){
            if(idx % 3 != 0){
                a += i;
            }else{
                idx = 0 ;
            }
            idx++;
        }
        
        return a;
    }
}
```

####    분석
-   주어진 int[]를 정렬하고 뒤집기만 하면 간단한 문제

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int minimumCost(int[] cost) {
        Arrays.sort(cost);
        int ans = 0;
        for(int i = 0;i < cost.length;i++){
            if(i % 3 == 2)continue;
            ans += cost[cost.length-1-i];
        }
        return ans;
    }
}
```


##   문제2
-   문제 링크 : [Count the Hidden Sequences](https://leetcode.com/contest/biweekly-contest-70/problems/count-the-hidden-sequences/)
####    정답

-   시간초과 정답

```java
class Solution {
    public int numberOfArrays(int[] differences, int lower, int upper) {
        
        int[] d = differences;
        int a = 0;
        
        
        for(int i=lower; i<upper; i++){
            boolean f = true;
            for(int j : d){
                i += j;
                if(i < lower || i > upper){
                    f = false;
                    break;
                }
            }
            if(f == true){
                a++;
            }
        }
        
        return a;
        
    }
}
```

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int numberOfArrays(int[] differences, int lower, int upper) {
        long max = 0, min = 0;
        long h = 0;
        for(int d : differences){
            h += d;
            max = Math.max(max, h);
            min = Math.min(min, h);
        }
        // h+min >= lower, h+max <= upper
        max = upper-max;
        min = lower - min;
        if(min > max)return 0;
        return (int)(max-min+1);
    }
}
```

-   skywalkert

```cpp
class Solution {
public:
    int numberOfArrays(vector<int>& differences, int lower, int upper) {
        typedef long long LL;
        LL L = 0, R = 0, cur = 0;
        for(int x: differences) {
            cur += x;
            if(cur < L) {
                L = cur;
            } else if(cur > R) {
                R = cur;
            }
        }
        LL p = R - L, q = upper - lower;
        return p <= q ? q - p + 1 : 0;
    }
};
```


##   문제3
-   문제 링크 : [K Highest Ranked Items Within a Price Range](https://leetcode.com/contest/biweekly-contest-70/problems/k-highest-ranked-items-within-a-price-range/)
####    정답
```java
```

####    분석
-   이런식의 2차원 배열 문제 연습이 필요함.

####    참고할 만한 정답

-   uwi

```java

class Solution {
    public List<List<Integer>> highestRankedKItems(int[][] a, int[] pricing, int[] start, int k) {
        int n = a.length, m = a[0].length;
        int[][] d = distMap(a, start[0], start[1]);
        List<int[]> items = new ArrayList<>();
        for(int i = 0;i < n;i++){
            for(int j = 0;j < m;j++){
                if(pricing[0] <= a[i][j] && a[i][j] <= pricing[1]){
                    if(d[i][j] < 500000){
                        items.add(new int[]{d[i][j], a[i][j], i, j});
                    }
                }
            }
        }
        Collections.sort(items, (x, y) -> {
            for(int i = 0;i < 4;i++) {
                if (x[i] != y[i]) return x[i] - y[i];
            }
            return 0;
        });
        List<List<Integer>> ret = new ArrayList<>();
        for(int i = 0;i < k && i < items.size();i++){
            ret.add(List.of(items.get(i)[2], items.get(i)[3]));
        }
        return ret;
    }

    public int[][] distMap(int[][] map, int sr, int sc)
    {
        int[] dr = { 1, 0, -1, 0 };
        int[] dc = { 0, 1, 0, -1 };
        int n = map.length;
        if(n == 0)return new int[0][0];
        int m = map[0].length;

        int[][] d = new int[n][m];
        int I = 999999999;
        for(int i = 0;i < n;i++) {
            Arrays.fill(d[i], I);
        }

        Queue<int[]> q = new ArrayDeque<int[]>();
        q.add(new int[]{sr, sc});
        d[sr][sc] = 0;

        while(!q.isEmpty()){
            int[] cur = q.poll();
            int r = cur[0], c = cur[1];
            for(int k = 0;k < dr.length;k++) {
                int nr = r + dr[k], nc = c + dc[k];
                if(nr >= 0 && nr < n && nc >= 0 && nc < m){
                    if(map[nr][nc] != 0 && d[nr][nc] > d[r][c] + 1) {
                        d[nr][nc] = d[r][c] + 1;
                        q.add(new int[]{nr, nc});
                    }
                }
            }
        }
        return d;
    }
}

```

-   skywalkert

```cpp
class Solution {
public:
    vector<vector<int>> highestRankedKItems(vector<vector<int>>& grid, vector<int>& pricing, vector<int>& start, int k) {
        int n = grid.size(), m = grid[0].size();
        vector<vector<int> > dis(n, vector<int>(m)), que, items;
        int sx = start[0], sy = start[1];
        dis[sx][sy] = 1;
        que.push_back({sx, sy});
        for(int i = 0; i < (int)que.size(); ++i) {
            auto &vec = que[i];
            int x = vec[0], y = vec[1];
            if(pricing[0] <= grid[x][y] && grid[x][y] <= pricing[1]) {
                items.push_back({dis[x][y], grid[x][y], x, y});
            }
            for(int dx = -1; dx <= 1; ++dx)
                for(int dy = -1; dy <= 1; ++dy) {
                    if(!!dx == !!dy)
                        continue;
                    int xx = x + dx, yy = y + dy;
                    if(xx < 0 || xx >= n || yy < 0 || yy >= m || !grid[xx][yy] || dis[xx][yy])
                        continue;
                    dis[xx][yy] = dis[x][y] + 1;
                    que.push_back({xx, yy});
                }
        }
        sort(items.begin(), items.end());
        vector<vector<int> > ret;
        for(int i = 0; i < (int)items.size() && i < k; ++i)
            ret.push_back({items[i][2], items[i][3]});
        return ret;
    }
};

```


##   문제4
-   문제 링크 : [Number of Ways to Divide a Long Corridor](https://leetcode.com/contest/biweekly-contest-70/problems/number-of-ways-to-divide-a-long-corridor/)
####    정답
```java
```

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int numberOfWays(String corridor) {
        char[] s = corridor.toCharArray();
        int n = s.length;

        List<Integer> ss = new ArrayList<>();
        for(int i = 0;i < n;i++){
            if(s[i] == 'S')ss.add(i);
        }
        if(ss.size() % 2 == 1 || ss.size() == 0){
            return 0;
        }
        final int mod = 1000000007;
        long ans = 1;
        for(int i = 1;i+1 < ss.size();i+=2){
            ans = ans * (ss.get(i+1) - ss.get(i)) % mod;
        }
        return (int)ans;
    }
}
```

-   skywalkert

```cpp

class Solution {
public:
    int numberOfWays(string seq) {
        const int mod = (int)1e9 + 7;
        int n = seq.size();
        vector<int> dp(n + 1), ctr(n + 1);
        dp[0] = ctr[0] = 1;
        for(int i = 1, c = 0; i <= n; ++i) {
            c += seq[i - 1] == 'S';
            if(c >= 2)
                dp[i] = ctr[c - 2];
            (ctr[c] += dp[i]) >= mod && (ctr[c] -= mod);
        }
        return dp.back();
    }
};
```