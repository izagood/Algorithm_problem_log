#   정답
```java

```

#   분석

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

#   참고할 만한 정답