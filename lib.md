#   Library

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

##  최소
```java
int min = Integer.MAX_VALUE;
if(min > a){
    min = a;
}
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