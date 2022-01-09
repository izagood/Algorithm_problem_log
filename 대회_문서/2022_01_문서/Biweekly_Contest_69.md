##    문제1 ⭕
-   문제 링크 : [2129. Capitalize the Title](https://leetcode.com/contest/biweekly-contest-69/problems/capitalize-the-title/)

####   정답
```java
class Solution {
    public String capitalizeTitle(String title) {
        
        /*
            공백으로 String[] 로 나누고 각각의 길이 3이상이면 첫번째 대문자로
            길이 1,2는 모두 소문자
        */
        String[] arr = title.split(" ");
        for(int i=0; i<arr.length; i++){
            if(arr[i].length() > 2){
                arr[i] = arr[i].toLowerCase();
                String first = arr[i].substring(0, 1);
                arr[i] = first.toUpperCase() + arr[i].substring(1);
            }else{
                arr[i] = arr[i].toLowerCase();
            }
        }
        
        String answer = "";
        
        for(String str : arr){
            answer += str + " ";
        }
        
        return answer.trim();
        
    }
}
```

####   분석


####   참고할 만한 정답
```cpp

class Solution {
public:
	string capitalizeTitle(string s) {
		int n = s.length(), i, j, k;
		for (i = 0; i < n; i++) {
			if (s[i] != ' ') {
				for (j = i; (j < n) && (s[j] != ' '); j++);
				if (j - i <= 2) {
					for (k = i; k < j; k++) {
						if ((s[k] >= 'A') && (s[k] <= 'Z')) s[k] += 'a' - 'A';
					}
				}
				else {
					if ((s[i] >= 'a') && (s[i] <= 'z')) s[i] -= 'a' - 'A';
					for (k = i + 1; k < j; k++) {
						if ((s[k] >= 'A') && (s[k] <= 'Z')) s[k] += 'a' - 'A';
					}
				}
				i = j - 1;
			}
		}
		return s;
	}
};
```


##    문제2 ⭕
-   문제 링크 : [2130. Maximum Twin Sum of a Linked List](https://leetcode.com/contest/biweekly-contest-69/problems/maximum-twin-sum-of-a-linked-list/)

####   정답
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
import java.util.*;
class Solution {
    public int pairSum(ListNode head) {
        
        /*
            짝수의 리스트
            짝 찾기 (n-1-i) 번째
        */
        
        List<Integer> list = new ArrayList<>();
        
        list.add(head.val);
        while(head.next != null){
            head = head.next;
            list.add(head.val);
        }
        
        int n = list.size();
        if(n == 2){
            return list.get(0) + list.get(1);
        }
        int loop = n/2;
        List<Integer> sumList = new ArrayList<>();
        for(int i=0; i<loop; i++){
            sumList.add(list.get(i) + list.get(n-1-i));
        }
        
        int max = Integer.MIN_VALUE;
        for(int num : sumList){
            if(num > max){
                max = num;
            }
        }
        
        
        return max;
    }
}
```

####   분석


##    문제3
-   문제 링크 : [2131. Longest Palindrome by Concatenating Two Letter Words](https://leetcode.com/contest/biweekly-contest-69/problems/longest-palindrome-by-concatenating-two-letter-words/)

####   정답
```java

class Solution {
    public int longestPalindrome(String[] words) {
        
        /*
            그냥 반복문으로 싹 돌면서 만드는 수 밖에 없을듯
            palindrome 판별 함수에 넣은 다음에 true인 애들 받아서
            length가 가장 긴거
        */
        int length = words.length;
        
        //합 문자의 개수 loop
        for(int i=0; i<length; i++){
            //조합 loop
            for(int j=0; j<length;j++){
                words[]
            }
        }
        
        return 0;
    }
    
    private boolean palindrome(String str){
        
        int length = str.length();
        String front = "";
        String back = "";
        
        if(length % 2 == 0){
            front = str.substring(0, length);
            back = str.substring(length);
        }else{
            front = str.substring(0, length);
            back = str.substring(length + 1);
        }
        
        StringBuilder sb = new StringBuilder(back);
        back = sb.reverse().toString();
        
        if(front.equals(back)){
            return true;
        }else{
            return false;
        }
    }
}
```

####   분석


##    문제4
-   문제 링크 : [2132. Stamping the Grid](https://leetcode.com/contest/biweekly-contest-69/problems/stamping-the-grid/)
####   정답
```java
```

####   분석