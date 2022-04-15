###   정답(Solution)

-   재귀

```java
import java.util.*;
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> answer = new ArrayList<>();
        dfs(root, answer);
        return answer;
    }
    
    private void dfs(TreeNode root, List<Integer> answer){
        if(root != null){
            dfs(root.left, answer);
            dfs(root.right, answer);
            answer.add(root.val);
        }
        
    }
}
```

-   Stack 풀이

```java
import java.util.*;
class Solution {
    
    class Val{
        TreeNode node;
        int count = 0;
        Val(TreeNode node){
            this.node = node;
        }
    }
    
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> answer = new ArrayList<>();
        
        if(root == null) return answer;
        
        Stack<Val> st = new Stack<>();
        st.push(new Val(root));
        
        while(!st.isEmpty()){
            Val val = st.peek();
            if(val.count == 0){
                if(val.node.left != null) st.push(new Val(val.node.left));
                val.count++;
            }else if(val.count == 1){
                if(val.node.right != null) st.push(new Val(val.node.right));
                val.count++;
            }else{
                answer.add(val.node.val);
                st.pop();
            }
        }
        return answer;
    }
    
}
```

###   분석
-   dfs 의 가장 기본 풀이
