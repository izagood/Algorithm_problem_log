###   정답(Solution)
```java
    소스코드
```

###   분석
-   Node 정렬하는 방법

```java
Node SortedMerge(Node a, Node b){
    Node result = null;
        
    /* point to the last result pointer */
    Node lastPtrRef = result;
        
    while(1){
        if (a == null){
            lastPtrRef = b;
            break;
        }else if (b==null){
            lastPtrRef = a;
            break;
        }

        if(a.data <= b.data){
            MoveNode(lastPtrRef, a);
        }else{
            MoveNode(lastPtrRef, b);
        }
        
        /* tricky: advance to point to the next ".next" field */
        lastPtrRef = ((lastPtrRef).next);
    }

    return (result);
}
```

###   참고할 만한 정답
```java
    소스코드
```

###   비교 분석
-   비교 분석한 내용

###   비교 분석 반영
```java
    정답에 참고한 내용 추가
```



### 참조
[\[JAVA\] LeetCode 21 - Merge Two Sorted Lists](https://yenny-zzang.tistory.com/42)