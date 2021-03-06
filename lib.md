#   Library

#  CP 변수 규칙
```

의미없는 int : n + 숫자
문제에서 주어졌는데 너무 길때 int : 첫글자
for에서 사용되는 int : i, j, k
String : str
char : ch
Object : o

length : len + 숫자
배열 : arr + 숫자

List<String> : sList + 숫자
List<Integer> : iList + 숫자
-> 객체 첫글자 + List

Set<String> : sSet
Set<Integer> : iSet
-> 객체 첫글자 + Set

Map<String, Integer> : siMap
-> 객체 첫글자들 + Map

```

#  for문 패턴
-   인덱스로 변환하여야 할때
```java
for(int i=0; i<len; i++){}
```
-   단순 값 전체를 뽑아야할 때
```java
for(Obj o : objs){}
```

#  최대
```java
int max = Integer.MIN_VALUE;
if(max < a){
    max = a;
}
```

#  최대(이항)
```java
int c = Math.max(a,b);
```

#  최소
```java
int min = Integer.MAX_VALUE;
if(min > a){
    min = a;
}
```
#  최소(이항)
```java
int c = Math.min(a,b);
```

#  교환
```java
t = a;
a = b;
b = t;
```

#  dfs
```java
private 리턴 dfs(배열, 깊이, 타겟){
    if(깊이==){
        return 0;
    }else{
        return dfs(배열, 깊이+1, 타겟);
    }
}
```

#  stream -> arr
```java

//int[]
int[] answer = hs.stream().mapToInt(Integer::intValue).toArray(); // int[]만 특별히 toArray() 그대로 사용할 수 있다.
int[] answer = set.stream().sorted().mapToInt(Integer::intValue).toArray(); //정렬 추가

//String[]
String[] report = sset.stream().toArray(String[]::new);
```

#  숫자만 추출
```java
String intStr = str.replaceAll("[^0-9]", "");
```

#  정렬

```java
//중복 조건 정렬
return Arrays.stream(strings)
            .sorted((s1, s2) -> {
                if(s1.charAt(n) == s2.charAt(n)){
                    return s1.compareTo(s2);
                }
                return s1.charAt(n) - s2.charAt(n);
            }).toArray(String[]::new);
```

## 오름차순 정렬
```java
//오름차순 정렬
int[] answer = set.stream().sorted().mapToInt(Integer::intValue).toArray();

```

## 내림차순 정렬
```java
//내림차순 정렬
int[] cost = Arrays.stream(cost).boxed().sorted(Comparator.reverseOrder()).mapToInt(Integer::intValue).toArray();

//배열 정렬 후 역순으로 꺼내기
String[] arr = s.split("");
Arrays.sort(arr);
String str = "";
for(int i=arr.length-1; i>=0; i--){
    str += arr[i];
}

//StringBuilder 내림차순 정렬
char[] arr = s.toCharArray();
Arrays.sort(arr);
String str = new StringBuilder(new String(arr)).reverse().toString();

//n -1 -i 로 순차 for문 돌면서 역순조회하기
for(int i = 0;i < n;i++){
    if(i % 2 == 0){
        nums[i] = a[i/2]; //i/2를 사용하여 하나의 인덱스로 홀짝을 구분하여 index를 구분할 수 있다.
    }else{
        nums[i] = b[n/2-1-i/2]; //내림차순 조회
    }
}
```

#  숫자 자리수 구하기
```java
int len = (int)Math.log10(num) + 1;
```

#  중복 제거
```java
String[] report = Arrays.stream(report).distinct().toArray(String[]::new);
```

#   char 다루기
```java
//char int로 변환하기
char ch = '9';
int num = ch - '0'; //아스키코드 57 - 48 = 9
```

# 이분탐색
```java
int min = 0;
int max = 0;
for(int num : arr){
    if(num > max) max = num;
}

int answer = 0;
while(min <= max>){
    int mid = (min + max) / 2;

    int sum = 0;
    for(int num : arr){
        if(num > mid) sum += mid;
        else sum += num;
    }

    if(sum <= M>){
        min = mid + 1;
        answer = mid;
    }else{
        max = mid - 1;
    }
}
```