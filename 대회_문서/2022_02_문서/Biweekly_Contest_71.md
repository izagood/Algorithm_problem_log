##   문제1
-   문제 링크 : [Minimum Sum of Four Digit Number After Splitting Digits](https://leetcode.com/contest/biweekly-contest-71/problems/minimum-sum-of-four-digit-number-after-splitting-digits/)
####    정답
```java
import java.util.*;

class Solution {
    public int minimumSum(int num) {
        String str = String.valueOf(num);
        int len = str.length();
        String[] arr = str.split("");
        
        Arrays.sort(arr);
        
        StringBuilder lSb = new StringBuilder();
        StringBuilder rSb = new StringBuilder();
        
        for(int i=0; i<len; i++){
            if(i % 2 == 0){
                lSb.append(String.valueOf(arr[i]));
            }else{
                rSb.append(String.valueOf(arr[i]));
            }
        }
        
        return Integer.valueOf((lSb.toString())) + Integer.valueOf((rSb.toString()));
        
    }
}
```

####    분석
-   순열 조합 문제인줄 알았는데 좌우 번갈아 가면서 작은 숫자를 더해주면 되는 문제였음.

####    참고할 만한 정답

-   fextivity

```cpp
class Solution {
public:
    int minimumSum(int num) {
        int x = num / 1000, y = num / 100 % 10, z = num / 10 % 10, t = num % 10;
        vector <int> a = {x, y, z, t};
        sort(a.begin(), a.end());
        return (a[0] + a[1]) * 10 + (a[2] + a[3]);
    }
};
```

-   2499370956

```java
class Solution {
    public int minimumSum(int num) {
        int[] digits = new int[] {num % 10, (num / 10) % 10, (num / 100) % 10,  (num / 1000) % 10};
        Arrays.sort(digits);
        return 10 * digits[0] + 10 * digits[1] + digits[2] + digits[3];
    }
}
```

-   pa7adox

```cpp
class Solution {
public:
    int minimumSum(int num) {
        vector<int> digits;
        while (num) {
            digits.push_back(num % 10);
            num /= 10;
        }
        
        sort(digits.begin(), digits.end());
        int ans = digits[0] * 10 + digits[3] + digits[1] * 10 + digits[2];
        return ans;
    }
};
```

###   비교 분석
-   int[]로 풀었다가 0 때문에 String[]로 변환하였는데 10단위 1단위로 나눠서 더 해주면 위와 같은 풀이가 가능하다.

```java
    정답에 참고한 내용 추가
```


##   문제2
-   문제 링크 : [Partition Array According to Given Pivot](https://leetcode.com/contest/biweekly-contest-71/problems/partition-array-according-to-given-pivot/)
####    정답
```java
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        int p = pivot;
        int lCnt = 0;
        int gCnt = 0;
        int mCnt = 0;
        for(int i : nums){
            if(i>p){
                gCnt++;
            }else if(i<p){
                lCnt++;
            }else{
                mCnt++;
            }
        }
        
        int[] lArr = new int[lCnt];
        int[] gArr = new int[gCnt];
        int[] mArr = new int[mCnt];
        
        int lIdx = 0;
        int gIdx = 0;
        int mIdx = 0;
        for(int i : nums){
            if(i>p){
                gArr[gIdx] = i;
                gIdx++;
            }else if(i<p){
                lArr[lIdx] = i;
                lIdx++;
            }else{
                mArr[mIdx] = i;
                mIdx++;
            }
        }
        
        int[] a = new int[nums.length];
        int aIdx = 0;
        
        for(int i : lArr){
            a[aIdx] = i;
            aIdx++;
        }
        
        a[aIdx] = pivot;
        
        for(int i : mArr){
            a[aIdx] = i;
            aIdx++;
        }
        
        for(int i : gArr){
            a[aIdx] = i;
            aIdx++;
        }
        
        return a;
    }
}
```

####    분석
-   pivot을 기준으로 배열을 나누는 문제이다.
-   문제 요건에 따라 작성하였고 결과적으로 O(N)이기는 하지만 그렇게 좋아보이지 않는 코드...

####    참고할 만한 정답

-   2499370956

```java
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        List<Integer> list = new ArrayList<>();
        for (int i : nums) {
            if (i < pivot) {
                list.add(i);
            }
        }
        for (int i : nums) {
            if (i == pivot) {
                list.add(i);
            }
        }
        for (int i : nums) {
            if (i > pivot) {
                list.add(i);
            }
        }
        return list.stream().mapToInt(Integer::intValue).toArray();
    }
}
```

-   pa7adox

```cpp
class Solution {
public:
    vector<int> pivotArray(vector<int>& nums, int pivot) {
        vector<int> arr[3];
        for (int num : nums) {
            if (num < pivot)
                arr[0].push_back(num);
            else if (num == pivot)
                arr[1].push_back(num);
            else 
                arr[2].push_back(num);
        }
        
        vector<int> res;
        for (int i = 0; i < 3; i++)
            for (int num : arr[i])
                res.push_back(num);
        
        return res;
    }
};
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제3
-   문제 링크 : [Minimum Cost to Set Cooking Time](https://leetcode.com/contest/biweekly-contest-71/problems/minimum-cost-to-set-cooking-time/)
####    정답
-   풀이 못 함

####    분석
-   dfs 문제 같다.

####    참고할 만한 정답

-   2499370956

```java
class Solution {
    public int minCostSetTime(int startAt, int moveCost, int pushCost, int targetSeconds) {
        int out = Integer.MAX_VALUE;
        for (int i = 0; i <= 9999; i++) {
            int[] digits = new int[] {(i / 1000) % 10, (i / 100) % 10, (i / 10) % 10,  (i / 1) % 10};
            int seconds = digits[0] * 600 + digits[1] * 60 + digits[2] * 10 + digits[3];
            if (seconds != targetSeconds) {
                continue;
            }
            int cost = 0;
            int last = startAt;
            boolean skipZero = true;
            for (int d : digits) {
                if (d != 0 || (!skipZero)) {
                    if (last != d) {
                        last = d;
                        cost += moveCost;
                    }
                    cost += pushCost;
                    skipZero = false;
                }
            }
//            System.out.println("push " + i + " cost " + cost);
            out = Math.min(out, cost);
        }
        return out;
    }
}
```

-   pa7adox

```cpp
class Solution {
private:
    int push(int current, int need, int moveCost, int pushCost) {
        if (current == need)
            return pushCost;
        return moveCost + pushCost;
    }
    
public:
    int minCostSetTime(int startAt, int moveCost, int pushCost, int targetSeconds) {
        
        int ans = INT_MAX;
        
        for (int mn = 0; mn < 100; mn++) {
            for (int sc = 0; sc < 100; sc++) {
                if (mn * 60 + sc != targetSeconds)
                    continue;
                
                bool first = true;
                int num = mn * 100 + sc;
                vector<int> digits;
                while (num) {
                    digits.push_back(num % 10);
                    num /= 10;
                }
                
                reverse(digits.begin(), digits.end());
                
                int res = 0, cur = startAt;
                for (int d : digits) {
                    res += push(cur, d, moveCost, pushCost);
                    cur = d;
                }
                
                ans = min(ans, res);
            }
        }
        
        return ans;
    }
};
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제4
-   문제 링크 : [Minimum Difference in Sums After Removal of Elements](https://leetcode.com/contest/biweekly-contest-71/problems/minimum-difference-in-sums-after-removal-of-elements/)
####    정답
-   풀이 못 함

####    분석
-   

####    참고할 만한 정답

-   2499370956

```java
class Solution {
    public long minimumDifference(int[] nums) {
        int size = nums.length;
        int n = size / 3;
//        long[] sum = new long[size + 1];
//        for (int i = 0; i < size; i++) {
//            sum[i + 1] = sum[i] + nums[i];
//        }
        long[] minNSum = new long[size];
        long sum = 0;
        PriorityQueue<Integer> maxPQ = new PriorityQueue<>(Comparator.reverseOrder());
        for (int i = 0; i < n; i++) {
            sum += nums[i];
            maxPQ.add(nums[i]);
        }
        minNSum[n - 1] = sum;
        for (int i = n; i < 2 * n; i++) {
            sum += nums[i];
            maxPQ.add(nums[i]);
            sum -= maxPQ.remove();
            minNSum[i] = sum;
        }

        long[] maxNSum = new long[size];
        sum = 0;
        PriorityQueue<Integer> minPQ = new PriorityQueue<>(Comparator.naturalOrder());
        for (int i = 2 * n; i < 3 * n; i++) {
            sum += nums[i];
            minPQ.add(nums[i]);
        }
        maxNSum[2 * n] = sum;
        for (int i = 2 * n - 1; i >= n; i--) {
            sum += nums[i];
            minPQ.add(nums[i]);
            sum -= minPQ.remove();
            maxNSum[i] = sum;
        }

        long out = Long.MAX_VALUE;
        for (int i = n - 1; i < 2 * n; i++) {
            out = Math.min(out, minNSum[i] - maxNSum[i + 1]);
        }
        return out;
    }
}
```

-   pa7adox

```cpp
class Solution {
public:
    long long minimumDifference(vector<int>& nums) {
        int m = nums.size();
        int n = m / 3;
        
        vector<long long> ans(m, 0);
        
        multiset<int> first, second;
        long long sumFirst = 0;
        
        for (int i = 0; i < n; i++) {
            first.insert(-nums[i]);
            sumFirst += nums[i];
        }
        
        ans[n - 1] = sumFirst;
        for (int i = n; i < n + n; i++) {
            second.insert(nums[i]);
            while (-*first.begin() > *second.begin()) {
                int se = *second.begin();
                int fi = -*first.begin();
                first.erase(first.begin());
                second.erase(second.begin());
                first.insert(-se);
                second.insert(fi);
                sumFirst += se - fi;
            }
            ans[i] = sumFirst;
        }
        
        first.clear();
        second.clear();
        sumFirst = 0;
        
        for (int i = m - 1; i >= m - n; i--) {
            first.insert(nums[i]);
            sumFirst += nums[i];
        }
        
        long long answer = ans[n + n - 1] - sumFirst;
        
        for (int i = n + n - 1; i >= n; i--) {
            second.insert(-nums[i]);
            while (*first.begin() < -*second.begin()) {
                int fi = *first.begin();
                int se = -*second.begin();
                first.erase(first.begin());
                second.erase(second.begin());
                first.insert(se);
                second.insert(-fi);
                sumFirst += se - fi;
            }
            answer = min(answer, ans[i - 1] - sumFirst);
        }
        
        return answer;
    }
};
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```