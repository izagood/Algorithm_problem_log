-   알게된 함수 : Arrays.copyOfRange(배열, 시작인덱스(포함), 마지막인덱스(미포함));

-   사용 예시
```java
int[] array = {1, 5, 2, 6, 3, 7, 4};

int[] result = Arrays.copyOfRange(array, 2, 5);

//result = [2, 6, 3];

//시작인덱스는 포함이여 2부터 출력되고
//마지막인덱스는 미포함하여 3까지 출력된다.

```