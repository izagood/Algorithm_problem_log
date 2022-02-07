###   정답(Solution)
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
-   재귀