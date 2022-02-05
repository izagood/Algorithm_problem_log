###   정답(Solution)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        
        ListNode root = new ListNode();
        ListNode dummy = root;
        
        while(list1 != null || list2 != null){
            
            ListNode node = new ListNode();
            
            if(list1 == null){
                node.val = list2.val;
                list2 = list2.next;
            }else if(list2 == null){
                node.val = list1.val;
                list1 = list1.next;
            }else{
                if(list1.val <= list2.val){
                    node.val = list1.val;
                    list1 = list1.next;
                }else{
                    node.val = list2.val;
                    list2 = list2.next;
                }
            }
            
            root.next = node;
            root = root.next;
        }
        
        return dummy.next;
    }
}
```

###   분석
-   연결 리스트 문제
-   Node에 대해서 기본 지식이 있어야 풀 수 있는 문제

###   참고할 만한 정답
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1==null) return list2;
        if(list2==null) return list1;
        
      if(list1.val<list2.val)
      {
         list1.next=mergeTwoLists(list1.next,list2);
          return list1;
      }
        
        else
        {
            list2.next=mergeTwoLists(list1,list2.next);
            return list2;
        }
        
    }
}
```

###   비교 분석
-   재귀를 이용하여 풀었다.
-   정답들을 비교해 보니 내 풀이는 while문을 돌때마다 new로 ListNode를 생성해서 메모리를 조금 더 사용했다.

