###   정답(Solution)

-   Stack 풀이

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
import java.util.*;
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> answer = new ArrayList<>();
        Stack<TreeNode> stack = new Stack();
        while(root != null || !stack.isEmpty()){
            while(root != null){
                stack.push(root);
                root = root.left;
            }
            root = stack.pop();
            answer.add(root.val);
            root = root.right;
        }
        return answer;
    }
}
```

-   재귀 풀이

```java
import java.util.*;

class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> iList = new ArrayList<>();
        
        dfs(root, iList);
        
        return iList;
    }
    
    private void dfs(TreeNode root, List<Integer> iList){
        if(root == null){
            return;
        }
        dfs(root.left, iList);
        iList.add(root.val);
        dfs(root.right, iList);
    }
}
```

###   분석
-   DFS
-   가장 기본적인 문제