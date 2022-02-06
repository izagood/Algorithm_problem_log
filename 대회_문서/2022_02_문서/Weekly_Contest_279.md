##   문제1
-   문제 링크 : [Sort Even and Odd Indices Independently](https://leetcode.com/contest/weekly-contest-279/problems/sort-even-and-odd-indices-independently/)
####    정답
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int[] sortEvenOdd(int[] nums) {
        
        int len = nums.length;
        
        List<Integer> odd = new ArrayList<>();
        List<Integer> even = new ArrayList<>();
        
        for(int i=0; i<len; i++){
            if(i % 2 == 0){
                even.add(nums[i]);
            }else{
                odd.add(nums[i]);
            }
        }
        
        int[] eArr = even.stream().sorted().mapToInt(Integer::intValue).toArray();
        int eIdx = 0;
        
        int[] oArr = odd.stream().sorted(Comparator.reverseOrder()).mapToInt(Integer::intValue).toArray();
        int oIdx = 0;
        
        int[] a = new int[len];
        
        for(int i=0; i<len; i++){
            if(i % 2 == 0 ){
                a[i] = eArr[eIdx];
                eIdx++;
            }else{
                a[i] = oArr[oIdx];
                oIdx++;
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
    public int[] sortEvenOdd(int[] nums) {
        int n = nums.length;
        int[] a = new int[(n+1)/2];
        int[] b = new int[n/2];
        for(int i = 0;i < n;i++){
            if(i % 2 == 0){
                a[i/2] = nums[i]; //따로 idx를 생성하지 않고 i/2로 나눠져서 들어가게 한다...대박...
            }else{
                b[i/2] = nums[i];
            }
        }
        Arrays.sort(a);
        Arrays.sort(b);
        for(int i = 0;i < n;i++){
            if(i % 2 == 0){
                nums[i] = a[i/2];
            }else{
                nums[i] = b[n/2-1-i/2]; //와... 역순으로 꺼내오는걸 이렇게 하네...
            }
        }
        return nums;
    }
}
```

-   KimTaeyeon

```python
class Solution(object):
    def sortEvenOdd(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        n = len(nums)
        a = []
        b = []
        for i in range(n):
            if i % 2 == 0:
                a.append(nums[i])
            else:
                b.append(nums[i])
        a = sorted(a)
        b = sorted(b , reverse = True)
        o = []
        for i in range(n):
            if i % 2 == 0:
                o.append(a[i / 2])
            else:
                o.append(b[i / 2])
        return o
```

###   비교 분석
-   홀짝 index를 넣을때 i/2로 인덱스를 넣어주면 홀짝 따로 idx를 나누지 않아도 동일한 결과를 만들 수 있다.
-   int[]를 역순으로 가져올때 `길이 - 1 - 인덱스` 로 가져올 수 있다. `이 테크닉 너무 좋다`

```java
    정답에 참고한 내용 추가
```


##   문제2
-   문제 링크 : [Smallest Value of the Rearranged Number](https://leetcode.com/contest/weekly-contest-279/problems/smallest-value-of-the-rearranged-number/)
####    정답
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public long smallestNumber(long num) {
        
        if(String.valueOf(num).length() == 1){
            return num;
        }
        
        String str = "";
        boolean p = true;
        
        if(num < 0){
            str = String.valueOf(num).substring(1);
            p = false;
        }else{
            str = String.valueOf(num);
        }
        
        String[] arr = str.split("");
        
        
        int zCnt = 0;
            
        if(p){
            Arrays.sort(arr);
            for(String str1 : arr){
                if(str1.equals("0")){
                    zCnt++;
                }else{
                    break;
                }
            }
        }else{
            Arrays.sort(arr, Comparator.reverseOrder());
        }
        
        
        
        StringBuilder sb = new StringBuilder();
        
        for(int i=0; i<arr.length; i++){
            sb.append(arr[i]);
        }
        
        if(p){
            String temp = sb.toString();
            
            String t1 = temp.substring(0, zCnt);
            String t2 = temp.substring(zCnt, zCnt+1);
            String t3 = temp.substring(zCnt+1);
            
            temp = t2 + t1 + t3;
            return Long.valueOf(temp);
        }else{
            String temp = sb.toString();
            temp = "-" + temp;
            return Long.valueOf(temp);
        }
    }
}
```

####    분석
-   짝수일 경우 오름차순으로 정렬
-   홀수일 경우 내림차순으로 정렬
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public long smallestNumber(long num) {
        if(num == 0)return 0;
        char[] s = Long.toString(num).toCharArray();
        int[] f = new int[128];
        for(char c : s)f[c]++;
        if(f['-'] == 1){
            long v = 0;
            for(int c = '9';c >= '0';c--){
                for(int i = 0;i < f[c];i++){
                    v = v * 10 + c-'0';
                }
            }
            return -v;
        }else{
            long v = 0;
            for(int c = '1';c <= '9';c++) {
                if (f[c] > 0) {
                    v = v * 10 + c - '0';
                    f[c]--;
                    break;
                }
            }
            for(int c = '0';c <= '9';c++) {
                for(int i = 0;i < f[c];i++){
                    v = v * 10 + c-'0';
                }
            }
            return v;
        }
    }
}
```

-   KimTaeyeon

```python
class Solution(object):
    def smallestNumber(self, num):
        """
        :type num: int
        :rtype: int
        """
        a = list(str(num))
        b = 1
        if a[0] == '-':
            b = -1
            a = sorted(a[1:] , reverse = True)
            return int('-' + "".join(a))
        else:
            a = sorted(a)
            if len(a) == 1:
                return int(a[0])
            m = 0
            while a[m] == '0':
                m += 1
            b = a[m]
            for i in range(len(a)):
                if i != m:
                    b += a[i]
            return int(b)
```

###   비교 분석
-   String을 사용하지 않고 char를 사용해서 primitive 속도를 그대로 살릴 수 있도록 구현했다.
-   보수법을 사용하는건지 조금 더 확인해 봐야 함.

```java
    정답에 참고한 내용 추가
```


##   문제3
-   문제 링크 : [Design Bitset](https://leetcode.com/contest/weekly-contest-279/problems/design-bitset/)
####    정답
-   풀이 못 함

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Bitset {
    LST lst0;
    LST lst1;
    int n, one;

    public Bitset(int size) {
        lst0 = new LST(size);
        lst1 = new LST(size);
        lst0.setRange(size);
        n = size;
        one = 0;
    }

    public void fix(int idx) {
        if(!lst1.get(idx)){
            one++;
        }
        lst1.set(idx);
        lst0.unset(idx);
    }

    public void unfix(int idx) {
        if(lst1.get(idx)){
            one--;
        }
        lst0.set(idx);
        lst1.unset(idx);
    }

    public void flip() {
        LST d = lst0; lst0 = lst1; lst1 = d;
        one = n-one;
    }

    public boolean all() {
        return one == n;
    }

    public boolean one() {
        return one > 0;
    }

    public int count() {
        return one;
    }

    public String toString() {
        char[] ret = new char[n];
        for(int i = 0;i < n;i++){
            ret[i] = lst1.get(i) ? '1' : '0';
        }
        return new String(ret);
    }

    public class LST {
        public long[][] set;
        public int n;
        //	public int size;

        public LST(int n) {
            this.n = n;
            int d = 1;
            for(int m = n;m > 1;m>>>=6, d++);

            set = new long[d][];
            for(int i = 0, m = n>>>6;i < d;i++, m>>>=6){
                set[i] = new long[m+1];
            }
            //		size = 0;
        }

        // [0,r)
        public LST setRange(int r)
        {
            for(int i = 0;i < set.length;i++, r=r+63>>>6){
                for(int j = 0;j < r>>>6;j++){
                    set[i][j] = -1L;
                }
                if((r&63) != 0)set[i][r>>>6] |= (1L<<r)-1;
            }
            return this;
        }

        // [0,r)
        public LST unsetRange(int r)
        {
            if(r >= 0){
                for(int i = 0;i < set.length;i++, r=r+63>>>6){
                    for(int j = 0;j < r+63>>>6;j++){
                        set[i][j] = 0;
                    }
                    if((r&63) != 0)set[i][r>>>6] &= -(1L << r);
                }
            }
            return this;
        }

        public LST set(int pos)
        {
            if(pos >= 0 && pos < n){
                //			if(!get(pos))size++;
                for(int i = 0;i < set.length;i++, pos>>>=6){
                    set[i][pos>>>6] |= 1L<<pos;
                }
            }
            return this;
        }

        public LST unset(int pos)
        {
            if(pos >= 0 && pos < n){
                //			if(get(pos))size--;
                for(int i = 0;i < set.length && (i == 0 || set[i-1][pos] == 0L);i++, pos>>>=6){
                    set[i][pos>>>6] &= ~(1L<<pos);
                }
            }
            return this;
        }

        public boolean get(int pos)
        {
            return pos >= 0 && pos < n && set[0][pos>>>6]<<~pos<0;
        }

        public LST toggle(int pos)
        {
            return get(pos) ? unset(pos) : set(pos);
        }

        public int prev(int pos)
        {
            for(int i = 0;i < set.length && pos >= 0;i++, pos>>>=6, pos--){
                int pre = prev(set[i][pos>>>6], pos&63);
                if(pre != -1){
                    pos = pos>>>6<<6|pre;
                    while(i > 0)pos = pos<<6|63-Long.numberOfLeadingZeros(set[--i][pos]);
                    return pos;
                }
            }
            return -1;
        }

        public int next(int pos)
        {
            for(int i = 0;i < set.length && pos>>>6 < set[i].length;i++, pos>>>=6, pos++){
                int nex = next(set[i][pos>>>6], pos&63);
                if(nex != -1){
                    pos = pos>>>6<<6|nex;
                    while(i > 0)pos = pos<<6|Long.numberOfTrailingZeros(set[--i][pos]);
                    return pos;
                }
            }
            return -1;
        }

        private int prev(long set, int n)
        {
            long h = set<<~n;
            if(h == 0L)return -1;
            return -Long.numberOfLeadingZeros(h)+n;
        }

        private int next(long set, int n)
        {
            long h = set>>>n;
            if(h == 0L)return -1;
            return Long.numberOfTrailingZeros(h)+n;
        }

        @Override
        public String toString()
        {
            List<Integer> list = new ArrayList<>();
            for(int pos = next(0);pos != -1;pos = next(pos+1)){
                list.add(pos);
            }
            return list.toString();
        }
    }

}
```

-   KimTaeyeon

```cpp
const int N = 1e5 + 9;
class Bitset {
private:
    int a[N];
    bool rev;
    int ones , zeros;
    int sz;
public:
    Bitset(int size) {
        memset(a , 0 , sizeof(a));
        rev = false;
        zeros = size;
        ones = 0;
        sz = size;
    }
    
    void fix(int idx) {
        if ((rev && a[idx] == 1) || (!rev && a[idx] == 0)) {
            ++ones;
            --zeros;
        }
        if (rev) a[idx] = 0;
        else a[idx] = 1;
    }
    
    void unfix(int idx) {
        if ((rev && a[idx] == 0) || (!rev && a[idx] == 1)) {
            --ones;
            ++zeros;
        }
        if (rev) a[idx] = 1;
        else a[idx] = 0;
    }
    
    void flip() {
        rev = !rev;
        swap(ones , zeros);
    }
    
    bool all() {
        return zeros == 0;
    }
    
    bool one() {
        return ones > 0;
    }
    
    int count() {
        return ones;
    }
    
    string toString() {
        string o = "";
        for (int i = 0 ; i < sz ; ++i) {
            if (rev ^ (a[i] == 1)) {
                o += "1";
            } else o += "0";
        }
        return o;
    }
};

/**
 * Your Bitset object will be instantiated and called as such:
 * Bitset* obj = new Bitset(size);
 * obj->fix(idx);
 * obj->unfix(idx);
 * obj->flip();
 * bool param_4 = obj->all();
 * bool param_5 = obj->one();
 * int param_6 = obj->count();
 * string param_7 = obj->toString();
 */
```

###   비교 분석
-   비교 분석한 내용

```java
    정답에 참고한 내용 추가
```


##   문제4
-   문제 링크 : [Minimum Time to Remove All Cars Containing Illegal Goods](https://leetcode.com/contest/weekly-contest-279/problems/minimum-time-to-remove-all-cars-containing-illegal-goods/)
####    정답
-   풀이 못 함

####    분석
-   

####    참고할 만한 정답

-   uwi

```java
class Solution {
    public int minimumTime(String t) {
        char[] s = t.toCharArray();
        int n = s.length;
        int[] dp = new int[n+1];
        for(int i = 0;i < n;i++){
            dp[i+1] = Math.min(i+1, dp[i] + (s[i] == '1' ? 2 : 0));
        }
        int min = n;
        for(int i = 0;i <= n;i++){
            min = Math.min(min, dp[i] + n-i);
        }
        return min;
    }
}
```

-   KimTaeyeon

```cpp
const int N = 2e5 + 9;
class Solution {
private:
    int dp[N];
public:
    int minimumTime(string s) {
        int n = s.length();
        int z = 0;
        memset(dp , 0 , sizeof(dp));
        for (int i = n - 1 ; i >= 0 ; --i) {
            if (s[i] == '0') {
                z ++;
                dp[i] = dp[i + 1];
            } else {
                if (z > 0) {
                    dp[i] = dp[i + 1] + 2;
                    z--;
                } else {
                    dp[i] = dp[i + 1] + 1;
                }
            }
        }
        int ans = n;
        z = 0;
        int pre = 0;
        for (int i = 0 ; i < n ; ++i) {
            if (s[i] == '0') {
                z ++;
            } else {
                if (z > 0) {
                    pre += 2;
                    z--;
                } else {
                    pre++;
                }
            }
            ans = min(ans , dp[i + 1] + pre);
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