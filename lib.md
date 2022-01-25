#   Library

##  CP 변수 규칙
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

##  for문 패턴
-   인덱스로 변환하여야 할때
```java
for(int i=0; i<len; i++){}
```
-   단순 값 전체를 뽑아야할 때
```java
for(Obj o : objs){}
```

##  최대
```java
int max = Integer.MIN_VALUE;
if(max < a){
    max = a;
}
```

##  최대(이항)
```java
int c = Math.max(a,b);
```

##  최소
```java
int min = Integer.MAX_VALUE;
if(min > a){
    min = a;
}
```
##  최소(이항)
```java
int c = Math.min(a,b);
```

##  교환
```java
t = a;
a = b;
b = t;
```

##  dfs
```java
private 리턴 dfs(배열, 깊이, 타겟){
    if(깊이==){
        return 0;
    }else{
        return dfs(배열, 깊이+1, 타겟);
    }
}
```

##  stream -> arr
```java

//int[]
int[] answer = hs.stream().mapToInt(Integer::intValue).toArray(); // int[]만 특별히 toArray() 그대로 사용할 수 있다.
int[] answer = set.stream().sorted().mapToInt(Integer::intValue).toArray(); //정렬 추가

//String[]
String[] report = sset.stream().toArray(String[]::new);
```

##  숫자만 추출
```java
String intStr = str.replaceAll("[^0-9]", "");
```

##  정렬
```java
//정렬
int[] answer = set.stream().sorted().mapToInt(Integer::intValue).toArray();
//역순 정렬
int[] cost = Arrays.stream(cost).boxed().sorted(Comparator.reverseOrder()).mapToInt(Integer::intValue).toArray();
```