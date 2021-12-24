#   정답
```java
class Solution {
    public boolean isPalindrome(int x) {
        
        /*
        좌우 대칭
        */
        //음수
        if(x < 0){
            return false;
        }
        
        //0
        if(x == 0){
            return true;
        }
        
        String xStr = String.valueOf(x);
        int xLength = xStr.length();
        int halfXLength = xLength / 2;
        String leftXStr = "";
        String rightXStr = "";
        
        
        if(xLength % 2 == 0){
        //짝수 자리 숫자
        //좌우 딱 나눠짐
            //e.g. 123321
            leftXStr = xStr.substring(0, halfXLength);
            rightXStr = xStr.substring(halfXLength);
            String reverseRightXStr = reverseString(rightXStr);
            if(leftXStr.equals(reverseRightXStr)){
                return true;
            }else{
                return false;
            }
            
        }else{
        //홀수 자리 숫자
        //가운데 숫자 하나를 두고 나눠짐
            //e.g. 31213 121
            leftXStr = xStr.substring(0, halfXLength);
            rightXStr = xStr.substring(halfXLength + 1);
            String reverseRightXStr = reverseString(rightXStr);
            if(leftXStr.equals(reverseRightXStr)){
                return true;
            }else{
                return false;
            }
            
            
        }
        
    }
    
    private String reverseString(String str){
        
        String reverseStr = "";
        int length = str.length();
        char[] reverseCharArr = new char[length];
        int reverseIndex = 0;
        
        char[] charArr = str.toCharArray();
        
        for(int i=length-1; i>=0; i--){
            reverseCharArr[reverseIndex] = charArr[i];
            reverseIndex++;
        }
        
        reverseStr = String.valueOf(reverseCharArr);
        
        return reverseStr;
        
    }
}

```

#   분석
-   단순 역순 비교 문제

#   참고 할 만한 정답
1.  
```java
class Solution {
    public boolean isPalindrome(int x) {
        return new StringBuilder(Integer.toString(x)).reverse().toString().equals(Integer.toString(x));
    }
}
```
1.  
```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0)
            return false;
        if(x>=0 && x<10)
            return true;
        String s = Integer.toString(x);
        int i=0,j=s.length()-1;
        while(i<j){
            if(s.charAt(i)!=s.charAt(j))
                return false;
            i++;
            j--;
        }
        return true;
        
    }
   
}
```